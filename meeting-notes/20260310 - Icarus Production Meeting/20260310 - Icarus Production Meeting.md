## mar 10, 2026 09:00 GMT-5 | ICARUS Production Meeting

### Attendees

Alessandro Maria Ricci, Promita Roy, Vito di Benedetto, Tracy Usher, Daniel Carber

### Monitoring resource usage

| User Grid Usage History of the *Running Jobs by User* for the last 7 days: [link](https://fifemon.fnal.gov/monitor/d/000000053/experiment-batch-details?orgId=1&viewPanel=9&from=now-7d&to=now&var-experiment=icarus&var-pool=dune-global&var-pool=fifebatch) ![](images/image1.png) | User Job Efficiency History of the User Job Efficiency for the last 7 days: [link](https://fifemon.fnal.gov/monitor/d/000000022/experiment-efficiency-details?from=now-7d&to=now&var-experiment=icarus&var-pool=dune-global&var-pool=fifebatch&orgId=1&viewPanel=2) ![](images/image2.png) |
| ----- | ----- |
| **Icaruspro Jobs Exit Code** History of the icaruspro job exit code for the last 7 days: [link](https://landscape.fnal.gov/kibana/app/kibana#/dashboard/ba047b90-b8ca-11e7-989a-91951b87e80a?_g=\(refreshInterval:\(pause:!t,value:0\),time:\(from:now-4d,mode:relative,to:now\)\)&_a=\(description:'View%20jobs%20exit%20code,%20where%20they%20ran,%20and%20logs',filters:!\(\('$state':\(store:appState\),meta:\(alias:!n,disabled:!f,index:'fifebatch-history-*',key:pool,negate:!f,params:\(query:fifebatch,type:phrase\),type:phrase,value:fifebatch\),query:\(match:\(pool:\(query:fifebatch,type:phrase\)\)\)\),\('$state':\(store:appState\),meta:\(alias:!n,disabled:!f,index:'fifebatch-history-*',key:User,negate:!f,params:\(query:'icaruspro@fnal.gov',type:phrase\),type:phrase,value:'icaruspro@fnal.gov'\),query:\(match:\(User:\(query:'icaruspro@fnal.gov',type:phrase\)\)\)\),\('$state':\(store:appState\),meta:\(alias:!n,disabled:!f,index:'fifebatch-history-*',key:Jobsub_Group,negate:!f,params:\(query:icarus,type:phrase\),type:phrase,value:icarus\),query:\(match:\(Jobsub_Group:\(query:icarus,type:phrase\)\)\)\)\),fullScreenMode:!f,options:\(darkTheme:!f\),panels:!\(\(embeddableConfig:\(vis:\(colors:\(Cancelled:%23967302,Fail:%23BF1B00,Success:%23629E51\),legendOpen:!t\)\),gridData:\(h:15,i:'1',w:40,x:0,y:0\),id:'2f40f420-b8ca-11e7-989a-91951b87e80a',panelIndex:'1',type:visualization,version:'6.8.23'\),\(gridData:\(h:10,i:'2',w:24,x:24,y:15\),id:'569cca30-b8ca-11e7-989a-91951b87e80a',panelIndex:'2',type:visualization,version:'6.8.23'\),\(gridData:\(h:10,i:'3',w:24,x:0,y:15\),id:'65759a00-b8ca-11e7-989a-91951b87e80a',panelIndex:'3',type:visualization,version:'6.8.23'\),\(embeddableConfig:\(columns:!\(JobsubJobId,Owner,ExitCode,ExitSignal,MATCH_GLIDEIN_Site,MachineAttrMachine0,stdout,stderr\),sort:!\('@timestamp',desc\)\),gridData:\(h:30,i:'4',w:48,x:0,y:25\),id:'7e94c3c0-b8cb-11e7-989a-91951b87e80a',panelIndex:'4',type:search,version:'6.8.23'\),\(gridData:\(h:15,i:'5',w:8,x:40,y:0\),id:AWZpvkXbLj3wKbt0N_Vp,panelIndex:'5',type:visualization,version:'6.8.23'\)\),query:\(language:lucene,query:\(match_all:\(\)\)\),timeRestore:!f,title:'Fifebatch%20History',viewMode:view\)) | **SBN Data Pools**[link](https://fifemon.fnal.gov/monitor/d/rflbgV-iz/dcache-by-poolgroup?orgId=1&var-PoolGroup=SbnData2Pools&from=now-3h&to=now&refresh=5m) |
| ![](images/image3.png) | ![](images/image4.png) |
| Dcache Persistent Usage per user  Total is 114 TiB: [link](https://fifemon.fnal.gov/monitor/d/000000175/dcache-persistent-usage-by-vo?orgId=1&var-VO=icarus), Used space: 94.5 TiB (82.8%) |   |
| ![](images/image5.png) |  |

### **Production requests**

| 2025 Ongoing/Pending Production Requests |
| ----- |
| ![](images/image6.png) |
| **2026 Ongoing/Pending Production Requests** |
| ![](images/image7.png) |

Link to [spreadsheet](https://docs.google.com/spreadsheets/d/1ffBp475tEzlRilFs7xLhbevSZHjsuk1Dm5FGFIPWsFM/edit?gid=1567393491#gid=1567393491)  
Link to [github project](https://github.com/orgs/SBNSoftware/projects/49)

### 

POMS active campaigns [here](https://pomsgpvm02.fnal.gov/poms/show_campaigns/icarus/production)

### Notes

* 

### Requests

* Assigned:  
  * Request \#61 and 145 \[Thomas\]:  
    1. Missing SAM def for data caf \+ flat caf and MC caf (problems with metadata)  
         
  * Request \#86 \[Manuel/Ivan\]:  
    1. See \#75. Running (55% complete).  
    2. Submitted stage1\_caf  
          
  * Request \#123 \[Fatima\]:  
    1. Almost complete. 39% of the recovery is complete

              

  * Request \#5 \[Alessandro\]:  
    1. 2.8% complete

    

  * Request \#8 \[Alessandro\]:  
    1. 4.5% complete  
    2. *gen\_g4\_detsim\_stage0* runs on NERSC and *stage1\_larcv* runs on FermiGrid, they can save in SLAC. Daniel must check with Justin.

    

  * Request \#9 \[Antonio/Alessandro\]:  
    1. The campaign started, but the jobs fail: inconsistency between sbn\_metadata\_script.sh and config file.

    

  * Request \#14 \[Thomas\]:  
    1. Test


  * Request \#15 \[Thomas\]:  
    1. Test


  * Request \#16 \[Promita\]:  
    1. Inconsistency between sbn\_metadata\_script.sh and config file as request \#9  
  *   
  * Request \#17-19 \[Promita\]:  
    1. Inconsistency between sbn\_metadata\_script.sh and config file as request \#9

### Action Items and Open issue

* Link to [action items](https://github.com/orgs/SBNSoftware/projects/32)

* **Storage:** 132 TiB free on SBNDataPool.

* \[Promita\] **Dataset already deleted (+ some more datasets):**  
* Mike Mooney and team: 

  Transferring  **icaruspro\_production\_v09\_89\_01\_01\_2024A\_ICARUS\_BNB\_nue\_MC\_FRFIX\_stage1** to tape

  Following the transfer: the dataset worth **35TB** can be deleted from SBNDataPool (Promita and Vito) **(DONE)**

* Transferring **icarus\_RWMStudies\_production\_Run2\_BNBMinbias\_v09\_91\_02\_02\_stage1** to tape prior to deletion (will free up \~**14TB**)   (Promita and Vito) **(DONE)**  
* Deleting **Icaruspro\_2024\_Run2\_production\_Reproc\_Run2\_v09\_89\_01\_01p03\_bnbminbias\_stage1** (will free up to \~**11TB**) **(DONE)**  
* **RHC sample with previous icaruscode v09\_89\_02\_00p01 deleted (15TB)**  
* icaruspro\_production\_v09\_89\_02\_00p01\_2025A\_ICARUS\_NuMI\_RHC\_MC\_NuMI\_RHC\_larcv, icaruspro\_production\_v09\_89\_02\_00p01\_2025A\_ICARUS\_NuMI\_RHC\_MC\_NuMI\_RHC\_stage1, (larcv \+ stage1 **20TB**)  
* icaruspro\_production\_v09\_89\_01\_01p02\_2024A\_ICARUS\_NuMI\_MC\_FRFIX\_NuMI\_MC\_FRFIX\_larcv, (**10TB**)  
* icaruspro\_production\_v09\_89\_02\_00p01\_2025A\_ICARUS\_NuMI\_FHC\_MC\_NuMI\_FHC\_larcv,calibtuples, caf, flatcafs, (**19 TB**)  
* icaruspro\_production\_v09\_89\_01\_01p02\_2024A\_ICARUS\_NuMI\_nue\_MC\_FRFIX\_NuMI\_nue\_MC\_FRFIX\_larcv (**3.5 TB)**  
* icaruspro\_production\_v09\_83\_01\_2024A\_ICARUS\_MPVMPR\_MC\_2024A\_MPVMPR\_MC\_larcv (**4.7 TB**)  
* Data campaigns deleted:   
              /pnfs/sbn/data/sbn\_fd/poms\_production/data/TriggerTest/  
               /pnfs/sbn/data/sbn\_fd/poms\_production/data/Data\_Run3\_11816\_allPMT (2.8 TB)  
               /pnfs/sbn/data/sbn\_fd/poms\_production/data/Data\_Run3\_11813\_allPMT (3.6 TB)  
               /pnfs/sbn/data/sbn\_fd/poms\_production/data/Run3 (69 TB)  
    
    
* \[Daniel\] SLAC has only 143 TB available over 1.2 PB\! But maybe it is possible to recover some space.

* \[Vito/Alessandro\] Chilgenb is in SBND and is no longer in ICARUS. Check if he is still active and the files can be removed. About Chris (chilgenb) files, there are many in /pnfs/icarus/persistent/sidecrt Files there are also from many users. Francesco Poppi and Laura Pasqualini.

* \[Promita/Thomas\] **Transfer of the larcv files of the SBN Spring Production to Polaris (ALCF) disk storages:**  
  * Run 2 data off-beam (SBN Production):  
    Icaruspro\_2025\_wcdnn\_production\_Reproc\_Run2\_SBN\_2\_v10\_06\_00\_06p03\_offbeambnbmajority\_larcv – 46 TB **\-\> DONE**  
  * Run 2 data on-beam (SBN Production):  
    Icaruspro\_2025\_wcdnn\_production\_Reproc\_Run2\_SBN\_2\_v10\_06\_00\_06p03\_offbeambnbmajority\_larcv  (on scratch) \-\> ONGOING  
  * ICARUS MC Overlays with v10\_06\_00\_06p01:  
    production\_mc\_2025A\_ICARUS\_Overlays\_BNB\_MC\_RUN2\_summer\_2025\_v10\_06\_00\_06p01\_larcv – 15 TB \-\> ONGOING  
  * There is traffic along the network and the transfer is slow.

* \[Promita/Alessandro\] **Transfer the following files (SBN Spring Production) to tape:**  
  * Run 2 data on-beam (note: request with calibration ntuples):  
    Icaruspro\_2025\_wcdnn\_production\_Reproc\_Run2\_SBN\_wCalib\_v10\_06\_00\_04p03\_bnbmajority\_larcv – 51 TB \-\> ONGOING  
  * Run 2 data off-beam (note: first request without calibration ntuples):  
    Icaruspro\_2025\_wcdnn\_production\_Reproc\_Run2\_SBN\_v10\_06\_00\_01p05\_offbeambnbmajority\_larcv – 45 TB  
  * Run 2 data on-beam (note: first request, without calibration ntuples):  
    Icaruspro\_2025\_wcdnn\_production\_Reproc\_Run2\_SBN\_v10\_06\_00\_01p05\_bnbmajority\_larcv – 58 TB

* \[Matheus/Giuseppe\] SBND is using some space in SBNDataPool. Some SBND datasets can be deleted \-\> 6 TiB can be recovered Totally we **recovered 22 TiB**.

* \[Vito/Antonio\] **Transfer of Run2 compressed files to Tape** **(420 TB), some TBs in DataPool2 as well** 100% complete \-\> Deleting on disk ongoing  
  The transfer to tape has been split by data stream, the selection was based on origin path, we can update the config to delete the BNB data streams selectively, we have  
  run2\_compressed\_bnbmajority\_SBNDATA \-\> DELETED run2\_compressed\_bnbmajority\_SBNDATA2 \-\> DELETED  
  run2\_compressed\_bnbminbias\_SBNDATA  
  run2\_compressed\_bnbminbias\_SBNDATA2  
  run2\_compressed\_offbeambnbmajority\_SBNDATA  
  run2\_compressed\_offbeambnbmajority\_SBNDATA2  
  run2\_compressed\_offbeambnbminbias\_SBNDATA  
  run2\_compressed\_offbeambnbminbias\_SBNDATA2  
  SBNDATA/SBNDATA2 suffix is to select files from one of SBNDataPools/SBNData2Pools  
  **Keep a subset of bnbmajority compressed raw data (run 9435\)**  
  (83 files of bnbmajority strems present a mismatch between tape and disk version, they have not been deleted)

### CNAF

* **RUN3 Processing**:   
  **Valerio and his team:** they have processed 100% of on- and off-beam, both bnbmajority and bnbminbias. Now the Italian team is processing the Calibration. Then, stage1 and caf will be reprocessed. **CNAF is full at 99%.**


### Keepup

* \[Ivan\]:   
  * not yet started with wcdnn framework: to do **getting everything running from github**  
    **Running fine**  
* \[Promita\]: update the available samples in SBN Production wiki.

### Infrastructure

* \[Mateus\]: **ICARUS data available on the SBN SAM instance.** SBND has developed scripts to help with the migration, so it might be good to coordinate with them how to move forward. CONTACT MATEUS

### Software

* \[Tracy\]: The icaruscode release status is in progress.  
* \[Matteo\]: *icaruscode* reproducibility: ongoing. Here [details](https://shortbaseline.slack.com/docs/T7P7C3UAK/F0A0K0PRR16). Matteo checks with Jacob Smith, the release manager.

### Computing

* \[Vito\]:

	Token in FTS tested but not used in production for the moment.  
Files must be transferred manually to NERSC. Rucio is setting up to transfer files with NERSC. Rucio also uses a proxy, need to use tokens.  
**New disk space available for ICARUS, SBND and Dune in LNCC in San Paolo in Brazil, cluster SDumont. Began the setup and tests.**  
Updated SAM configuration to run jobs with input files at NERSC.  
The files in Resilient are deleted after 30 days automatically if they are not used.