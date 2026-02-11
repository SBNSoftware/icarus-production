# icarus-production
The repository is intended to support ICARUS production activities. The aims of repository are is to be a reference for the ICARUS production team.
- Usefull scripts must be store [here](https://github.com/SBNSoftware/sbnutil),
- [track issues](https://github.com/SBNSoftware/icarus-production/issues)
- manage
  - [action items](https://github.com/orgs/SBNSoftware/projects/32)
  - [production requests](https://github.com/orgs/SBNSoftware/projects/49)
- develop a wiki to keep and share our know-how, for exmaple:
  - defining a 	diagnostics procedure
  - common solutions to problems
- track meetings' notes:
  - [20251202](<meeting-notes/20251202 - Icarus Production Meeting/20251202 - Icarus Production Meeting.md>)
  - [20251125](<meeting-notes/20251125 - Icarus Production Meeting/20251125 - Icarus Production Meeting.md>)
  - [20251104](<meeting-notes/20251104 - Icarus Production Meeting/20251104 - Icarus Production Meeting.md>)
  - [20251028](<meeting-notes/20251028 - Icarus Production Meeting/20251028 - Icarus Production Meeting.md>)
  - [20251007](<meeting-notes/20251007 - Icarus Production Meeting/20251007 - Icarus Production Meeting.md>)
  - [20250930](<meeting-notes/20250930 - Icarus Production Meeting/20250930 - Icarus Production Meeting.md>)
  - [20250923](<meeting-notes/20250923 - Icarus Production Meeting/20250923 - Icarus Production Meeting.md>)
  - [20250916](<meeting-notes/20250916 - Icarus Production Meeting/20250916 - Icarus Production Meeting.md>)
  - [20250909](<meeting-notes/20250909 - Icarus Production Meeting/20250909 - Icarus Production Meeting.md>)
  - [20260210](<meeting-notes/20260210 - Icarus Production Meeting/20260210 - Icarus Production Meeting.md>)


Sample requests are submitted via [the production request form](https://docs.google.com/forms/d/e/1FAIpQLScqdJRTznIZHRXsRsVegg_DEsHiEmdIh_p1y7uZS76_f2y1qw/viewform), and open requests are listed in [this spreadsheet](https://docs.google.com/spreadsheets/d/17mFPGsP7gw4GRLSCwIL15QrtUnLVri_2k2Wjzhd6Ork).

For newcomers, here we should list usefull materials:
- A basic POMS [guide](https://github.com/SBNSoftware/icarus_production_guide)
- The POMS [wiki](https://github.com/fermitools/poms/wiki) in github repository
- A more complete SBND-focused [guide](https://docs.google.com/document/d/1faX8JG3wHwjWl69GtFvojW2zB_IJ3zL0p8DzpwG93bk/edit?tab=t.0#heading=h.8u5f5oi2k2ce)

## Frequently Asked Questions (FAQ)

## How to delete datasets?

- **If the dataset is declared on samweb**, use the following command to retire the dataset:
  
  ```bash
  sam_retire_dataset -e sbn -v --name <defname>
  ```

  This command will:
  - Remove the dataset from SAMWeb
  - Delete the associated files from the storage
  
  **Note:** Folders will not be deleted automatically. It is your responsibility to remove them manually.

- **If the dataset is not declared on samweb**, you can simply use the `rm` command to delete it.

## How to get the samweb datasets residing in a filesystem path?

You can retrieve the datasets iteratively using the following command:

```bash
samweb -e sbn get-metadata --json $(samweb -e sbn list-files "full_path like 'dcache:/pnfs/sbn/data/sbn_fd/poms_production/2023A_ICARUS_BNB_Intime_Cosmics/%' and Dataset.Tag != 'icaruspro_production_v09_72_00_04_2023A_ICARUS_BNB_Intime_Cosmics_small_BNB_sample_calibtuple' and Dataset.Tag != 'icaruspro_production_v09_72_00_04_2023A_ICARUS_BNB_Intime_Cosmics_small_BNB_sample_caf' with limit 1") 2> /dev/null | jq -r '."Dataset.Tag"' 2> /dev/null
```

This command will:
- Pick-up the first file with the following constraints:
  - with a path compatible with the specified one
  - not belonging to the specified datasets (`Dataset.Tag`)
- For the selected file get the metadata and pick-up `Dataset.Tag` field

## How to move samweb dataset from disk to tape?

The suggested way is to use FTS. A FTS service can be run on `icarusprodgpvm01`. In that machine, there is a `FTS/FTS_config` folder containing all the files to run the service. The two relevant files are `run_fts_container.sh`, `fts.conf` and `sam_cp.cfg`.

- `run_fts_container.sh`: it used to run the FTS container using `podman`. In the files, the paths where the files resides have to specified in order to be mounted on the container

```
#----------------------------------------
# Start FTS from a podman container image
#----------------------------------------
#
# Adapted from ICARUS FTS setup on evb05
#
# Disclaimer:
# FTS is old, and can not be run on EL9 without significant complications.
# A prebuilt FTS container image is provided to work with Podman.
# To install on if-globusdtn machine, run as user `icaruspro`:
#   podman pull imageregistry.fnal.gov/sam-zerg/fermifts:latest
#
# Note:
# A -v mount line is needed for each local or pnfs directory that FTS needs.
# These can be deduced from the configuration files:
#  fts.conf
#  sam_cp.cfg
#

host=$(hostname -s)
echo "Starting FTS podman container image on ${host}"

# setting the volume paths inside the container to be the same
# matching between actual location and relative paths inside
# syntax: -v /HOST-DIR:/CONTAINER-DIR

# these are real locations on the current host
# using the same as the legacy FTS setup
fts_x509_proxy_dir=/opt/icaruspro/
fts_log_dir=/exp/icarus/data/users/icaruspro/FTS/logs/${host}/fts_logs
fts_db_dir=/var/tmp
fts_samcp_log_dir=/var/tmp
fts_config_dir=~icaruspro/FTS/${host}
fts_dropbox_dir=/pnfs/sbn/data/sbn_fd/poms_production/data/SummerShutdown
fts_dropbox_dir2=/pnfs/icarus/scratch/users/icaruspro/poms_production/data/keepup/v09_63_00_02p04

# copy config files into host-specific config directory
# this is not stricly necessary, but keeps things tidy?
mkdir -p ${fts_config_dir}
cp ${PWD}/fts.conf ${PWD}/sam_cp.cfg ${fts_config_dir}/

# additional things the run command does:
# - set hostname inside the container as ${host}
# - set $USER inside the container as current user
# - set container name to fts_${host}
# - expose port 8787 for localhost:8787 status page

podman run \
       -v ${fts_log_dir}:/opt/fts/fts_logs \
       -v ${fts_db_dir}:/opt/fts/fts_db \
       -v ${fts_config_dir}:/opt/fts/fts_config \
       -v ${fts_dropbox_dir}:/storage \
       -v ${fts_dropbox_dir2}:/storage2 \
       -v ${fts_samcp_log_dir}:/var/tmp \
       -v ${fts_x509_proxy_dir}:/opt/fts/fts_proxy \
       -p 8787:8787 \
       -d \
       --network slirp4netns:port_handler=slirp4netns \
       --hostname ${host} \
       --env USERNAME=${USER} \
       --name fts_${host} \
       --replace \
       fermifts
```

- `fts.conf`: it is the configuration file for FTS. In the file, several `filetypes` have to be specfified. For each `filetype`, there will a dedicate section specifing the relevant parameters

```
[main]
experiment=icarus
log-file = /opt/fts/fts_logs/fts_${hostname}
filetypes = SummerShutdown recovery
samweb-url = https://samicarus.fnal.gov:8483/sam/icarus/api
sam-web-registry-base-url = https://samicarus.fnal.gov:8483/sam_web_registry
x509-client-certificate = /opt/fts/fts_proxy/icaruspro.Production.proxy
x509-client-key = /opt/fts/fts_proxy/icaruspro.Production.proxy

local-db = /opt/fts/fts_db/${hostname}.db

enable-web-interface = True
enable-state-graph = True
web-interface-port = 8787
#allowed-web-ip = 131.225.*

#transfer-limits = enstore:1
#max-transfer-limit = 10
transfer-retries = 3
transfer-retry-interval = 300

scanner-queue-limit = 40000
scanner-max-limit = 250000

graphite-stats-server = fifemondata.fnal.gov:2004
service_name = fts_${hostname}

[filetype SummerShutdown]
scan-dirs = /storage
scan-interval = 10
scan-delay = 10
scan-file-patterns = *.root
scan-exclude-file-patterns = *.json RootDAQOut-*.root TFileService-*.root
extract-metadata = True
metadata-extractor = json-file-wait
transfer-to = enstore:/pnfs/icarus/archive/sbn/sbn_fd/${file_type}/SummerShutdown_2024/${file_format}/${file_id[8/2]}
erase-after-days = .01

[filetype recovery]
scan-dirs = /storage2
scan-interval = 10
scan-delay = 10
scan-file-patterns = data*.root
scan-exclude-file-patterns = *.json RootDAQOut-*.root TFileService-*.root
extract-metadata = True
metadata-extractor = json-file-wait
transfer-to = enstore:/pnfs/icarus/archive/sbn/sbn_fd/${file_type}/${file_format}/${data_tier}/${data_stream}/${production.type}/${production.name}/${icarus_project.software}/${icarus_project.name}/${icarus_project.stage}/${icarus_project.version}/${run_number[8/2]}
erase-after-days = .01
```

- `sam_cp.cfg`: it is the configuration file for samweb. Here there is the mapping between samweb storage element and the surl

```
[sam_cp]
logfile=/var/tmp/sam_cp_${USERNAME}.log
debug=1

[dcache_scratch_dst]
dstre: dcache:/pnfs/icarus/scratch/
dstrepl: root://fndcadoor.fnal.gov:1094/pnfs/fnal.gov/usr/icarus/scratch/

[dcache_persistent_dst]
dstre: dcache:/pnfs/icarus/persistent/
dstrepl: root://fndcadoor.fnal.gov:1094/pnfs/fnal.gov/usr/icarus/persistent/

[dcache_src]
srcre: dcache:/pnfs/icarus/
srcrepl: root://fndcadoor.fnal.gov:1094/pnfs/fnal.gov/usr/icarus/

[enstore_dst]
dstre: enstore:/pnfs/icarus/archive/
dstrepl: root://fndcadoor.fnal.gov:1094/pnfs/fnal.gov/usr/icarus/archive/

[dcache_sbn_src]
srcre: dcache:/pnfs/sbn
srcrepl: root://fndcadoor.fnal.gov:1094/pnfs/fnal.gov/usr/sbn
```
