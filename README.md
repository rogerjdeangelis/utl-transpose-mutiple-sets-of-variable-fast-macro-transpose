# utl-transpose-mutiple-sets-of-variable-fast-macro-transpose
Transpose mutiple sets of variable fast macro transpose

    Transpose multiple sets of variables fast macro transpose                                                        
                                                                                                                     
    github                                                                                                           
    https://tinyurl.com/wb5nq3z                                                                                      
    https://github.com/rogerjdeangelis/utl-transpose-mutiple-sets-of-variable-fast-macro-transpose                   
                                                                                                                     
    utl_transpose macro by                                                                                           
    AUTHORS: Arthur Tabachneck, Xia Ke Shan, Robert Virgile and Joe Whitehurst                                       
                                                                                                                     
    SAS Forum                                                                                                        
    https://tinyurl.com/s9nqkxc                                                                                      
    https://communities.sas.com/t5/SAS-Enterprise-Guide/Roll-up-two-rows-into-one/m-p/604612                         
                                                                                                                     
    macros                                                                                                           
    https://tinyurl.com/y9nfugth                                                                                     
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                       
                                                                                                                     
    *_                   _                                                                                           
    (_)_ __  _ __  _   _| |_                                                                                         
    | | '_ \| '_ \| | | | __|                                                                                        
    | | | | | |_) | |_| | |_                                                                                         
    |_|_| |_| .__/ \__,_|\__|                                                                                        
            |_|                                                                                                      
    ;                                                                                                                
                                                                                                                     
    data have;                                                                                                       
       input name$ semester s1-s3 grade$;                                                                            
    cards4;                                                                                                          
    Bob 1 82 85 88 B                                                                                                 
    Bob 2 78 88 98 B                                                                                                 
    Tom 1 80 90 90 A                                                                                                 
    Tom 2 77 87 78 B                                                                                                 
    Jon 1 88 72 95 B                                                                                                 
    ;;;;                                                                                                             
    run;quit;                                                                                                        
                                                                                                                     
     WORK.HAVE total obs=5                                                                                           
                                                                                                                     
       NAME    SEMESTER    S1    S2    S3    GRADE                                                                   
                                                                                                                     
       Bob         1       82    85    88      B                                                                     
       Bob         2       78    88    98      B                                                                     
       Tom         1       80    90    90      A                                                                     
       Tom         2       77    87    78      B                                                                     
       Jon         1       88    72    95      B                                                                     
                                                                                                                     
    *            _               _                                                                                   
      ___  _   _| |_ _ __  _   _| |_                                                                                 
     / _ \| | | | __| '_ \| | | | __|                                                                                
    | (_) | |_| | |_| |_) | |_| | |_                                                                                 
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                
                    |_|                                                                                              
    ;                                                                                                                
                                                                                                                     
     WORK.WANT total obs=3                                                                                           
                                                                                                                     
              Subjects and Grades 1st Semester      Subjects and Grades 1st 1st Semester                             
            ==================================     ======================================                            
                                                                                                                     
      NAME    S1_1    S2_1    S3_1    GRADE_1        S1_2    S2_2    S3_2    GRADE_2                                 
                                                                                                                     
      Bob      82      85      88        B            78      88      98        B                                    
      Tom      80      90      90        A            77      87      78        B                                    
      Jon      88      72      95        B             .       .       .                                             
                                                                                                                     
    *                                                                                                                
     _ __  _ __ ___   ___ ___  ___ ___                                                                               
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                              
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                              
    | .__/|_|  \___/ \___\___||___/___/                                                                              
    |_|                                                                                                              
    ;                                                                                                                
                                                                                                                     
    %utl_transpose(data=have, out=want, by=name, id=semester, delimiter=_,var=s1-s3 grade);                          
                                                                                                                     
