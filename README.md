# utl-extracting-data-from-a-json-file-from-api-using-r-lists
Problem: Create a SAS dataset for each of the three data structures in a JSON file.

    Extracting data from a json file using r lists                                                                             
                                                                                                                               
    Problem: Create a SAS dataset for each of the three data structures in a JSON file.                                        
                                                                                                                               
    SAS is not well suited to deal with nested JSON structures.                                                                
    Python and R have a native list structures to deal with these JSON files.                                                  
                                                                                                                               
    SAS Forum                                                                                                                  
    https://tinyurl.com/y2p3mrvr                                                                                               
    https://communities.sas.com/t5/SAS-Programming/Extracting-Data-from-JSON-File-from-API/m-p/566674                          
                                                                                                                               
    macros                                                                                                                     
    https://tinyurl.com/y9nfugth                                                                                               
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                 
                                                                                                                               
    Other JSON repos                                                                                                           
    https://tinyurl.com/yck67hm7                                                                                               
    https://github.com/rogerjdeangelis?utf8=%E2%9C%93&tab=repositories&q=json+in%3Aname&type=&language=                        
                                                                                                                               
    *_                   _                                                                                                     
    (_)_ __  _ __  _   _| |_                                                                                                   
    | | '_ \| '_ \| | | | __|                                                                                                  
    | | | | | |_) | |_| | |_                                                                                                   
    |_|_| |_| .__/ \__,_|\__|                                                                                                  
            |_|                                                                                                                
    ;                                                                                                                          
                                                                                                                               
    d:/json/jsnlst.json                                                                                                        
                                                                                                                               
    filename ft15f001 "d:/json/jsnlst.json";                                                                                   
    parmcards4;                                                                                                                
    {"ndcStatus":{"ndc11":"00364666854","status":"OBSOLETE","active":"NO","rxnormNdc":"YES",                                   
    "rxcui":"312656","conceptName":"Promazine 50 MG/ML Injectable Solution",                                                   
    "conceptStatus":"RETIRED","sourceList":{"sourceName":["MMSL","MMX","RXNORM","VANDF"]},                                     
    "altNdc":"N","comment":"","ndcHistory":[{"activeRxcui":"","originalRxcui":"312656",                                        
    "startDate":"200706","endDate":"201101"}]}}                                                                                
    ;;;;                                                                                                                       
    run;quit;                                                                                                                  
                                                                                                                               
    HOW THIS FILE MAPS TO A R LIST                                                                                             
    ******************************                                                                                             
                                                                                                                               
    We have three data structures two lists and a data frame.                                                                  
    So lets create three SAS datasets.                                                                                         
                                                                                                                               
    LIST                                                                                                                       
                                                                                                                               
     $ ndcStatus:List of 11                                                                                                    
      ..$ ndc11        : chr "00364666854"                                                                                     
      ..$ status       : chr "OBSOLETE"                                                                                        
      ..$ active       : chr "NO"                                                                                              
      ..$ rxnormNdc    : chr "YES"                                                                                             
      ..$ rxcui        : chr "312656"                                                                                          
      ..$ conceptName  : chr "Promazine 50 MG/ML Injectable Solution"                                                          
      ..$ conceptStatus: chr "RETIRED"                                                                                         
                                                                                                                               
    LIST                                                                                                                       
                                                                                                                               
      ..$ sourceList   :List of 1                                                                                              
      .. ..$ sourceName: chr [1:4] "MMSL" "MMX" "RXNORM" "VANDF"                                                               
                                                                                                                               
      ..$ altNdc       : chr "N"                                                                                               
      ..$ comment      : chr ""                                                                                                
                                                                                                                               
    DATAFRAME                                                                                                                  
                                                                                                                               
      ..$ ndcHistory   :'data.frame':	1 obs. of  4 variables:                                                                  
      .. ..$ activeRxcui  : chr ""                                                                                             
      .. ..$ originalRxcui: chr "312656"                                                                                       
      .. ..$ startDate    : chr "200706"                                                                                       
      .. ..$ endDate      : chr "201101"                                                                                       
                                                                                                                               
    *            _               _                                                                                             
      ___  _   _| |_ _ __  _   _| |_                                                                                           
     / _ \| | | | __| '_ \| | | | __|                                                                                          
    | (_) | |_| | |_| |_) | |_| | |_                                                                                           
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                          
                    |_|                                                                                                        
    ;                                                                                                                          
                                                                                                                               
    THE DATASETS ONE FOR EACH DATA STRUCTURE IN THE JSON FILE                                                                  
    *********************************************************                                                                  
                                                                                                                               
    WORK.NDCSTAT_R total obs=1                                                                                                 
                                                                                                                               
        NDC11      STATUS  ACTIVE RXNORMNDC  RXCUI                CONCEPTNAME               CONCEPTSTATUS ALTNDC COMMENT       
                                                                                                                               
     00364666854  OBSOLETE   NO      YES     312656  Promazine 50 MG/ML Injectable Solution    RETIRED      N                  
                                                                                                                               
                                                                                                                               
    WORK.HISTORY_R total obs=1                                                                                                 
                                                                                                                               
      ACTIVERXCUI    ORIGINALRXCUI    STARTDATE    ENDDATE                                                                     
                                                                                                                               
                        312656         200706      201101                                                                      
                                                                                                                               
    WORK.SRCELST_R total obs=4                                                                                                 
                                                                                                                               
      SOURCENAME                                                                                                               
                                                                                                                               
        MMSL                                                                                                                   
        MMX                                                                                                                    
        RXNORM                                                                                                                 
        VANDF                                                                                                                  
                                                                                                                               
    *                                                                                                                          
     _ __  _ __ ___   ___ ___  ___ ___                                                                                         
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                        
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                        
    | .__/|_|  \___/ \___\___||___/___/                                                                                        
    |_|                                                                                                                        
    ;                                                                                                                          
                                                                                                                               
    * I put the lon column names into R labels and                                                                             
      then use those labes to rename SAS truncated column names;                                                               
    * much of this code is to pred data for output;                                                                            
                                                                                                                               
    %utl_submit_r64('                                                                                                          
       library();                                                                                                              
       library(rio);                                                                                                           
       library(Hmisc);                                                                                                         
       library(SASxport);                                                                                                      
       library(data.table);                                                                                                    
       want<-as.list(import("d:/json/jsnlst.json"));                                                                           
       ndcstat<-as.data.table(want$ndcStatus[c(1:7,9:10)]);                                                                    
       for (i in seq_along(ndcstat)) {label(ndcstat[[i]])<-colnames(ndcstat)[i]};                                              
       srcelst<-as.data.table(want$ndcStatus$sourceList);                                                                      
       for (i in seq_along(srcelst)) {label(srcelst[[i]])<-colnames(srcelst)[i]};                                              
       history<-as.data.table(want$ndcStatus$ndcHistory);                                                                      
       for (i in seq_along(history)) {label(history[[i]])<-colnames(history)[i]};                                              
       write.xport(ndcstat,history,srcelst,file="d:/xpt/want.xpt");                                                            
     ');                                                                                                                       
                                                                                                                               
    * convert xport file to SAS datasets, you can use single                                                                   
    'proc copy' but the variable names will be truncated;                                                                      
                                                                                                                               
    libname xpt xport "d:/xpt/want.xpt";  
    
    proc datasets lib=work mt=view mt=data noist;         
       delete __ren001 ndcstat history srcelst;                     
    run;quit;                                           
                                                
     /* need this if you rerun                       
     NOTE: Deleting WORK.__REN001 (memtype=DATA).    
     NOTE: Deleting WORK.WANT (memtype=VIEW).        
    */                                              
                                                

    data ndcstat_r;                                                                                                            
      %utl_rens(xpt.ndcstat);                                                                                                  
      set ndcstat;                                                                                                             
    run;quit;                                                                                                                  
    data history_r;                                                                                                            
      %utl_rens(xpt.history);                                                                                                  
      set history;                                                                                                             
    run;quit;                                                                                                                  
    data srcelst_r;                                                                                                            
      %utl_rens(xpt.srcelst);                                                                                                  
      set srcelst;                                                                                                             
    run;quit;                                                                                                                  
    libname xpt clear;                                                                                                         
                                                                                                                               
                                                                                                                               
                                                                                                                               
