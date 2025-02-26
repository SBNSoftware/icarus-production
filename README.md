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

For newcomers, here we should list usefull materials:
- A basic POMS [guide](https://github.com/SBNSoftware/icarus_production_guide)
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
