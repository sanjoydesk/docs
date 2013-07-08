Cygnite Framework User Guide 
=============================

Cygnite Robot Loader
=====================
Autoload your applications files is very easy with Cygnite framework. You need to register your files in 
configs/autoload.php. For example-


Register your Libraries and Classes
-----------------------------------

         Cygnite::loader()->register_classes(
                                            array(
                                                     'CF_Cache' => CF_SYSTEM.'>cygnite>libraries>cache>handler>CF_Cache'.EXT,
                                                     'CF_Authx' => APPVENDORSDIR.'>libs>CF_Authx'.EXT,
                                                     'CF_Common' => APPVENDORSDIR.'>libs>CF_Common'.EXT,
                                            )
                     ),
                     
                     
Register your Models dynamically into Cygnite Robot Loader
----------------------------------------------------------

          Cygnite::loader()->register_models(array(
                                    'Activerecords'=>'apps>models>activerecords.php',
                                    'Records'=>'apps>models>records.php'
                    ))
                    
                    
How to call Model or libraries ?
--------------------------------
Calling models and libraries is very easy with cygnite. For example if you want to call sayhello()-

           
        Cygnite::loader()->request('records')->sayhello();
        
        
Output :
Hellow World !!
     
     
