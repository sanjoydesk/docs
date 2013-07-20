  
  Cygnite Framework User Guide
  ----------------------------

   How to autoload libraries and Classes ?
   -----------------------------------------------
   Cygnite Framework core allow lazy loading files dynamically. So you can register multiple libraries into Cygnite Framework Robot Engine.
   All files will be dynamically autoloaded based on your needs. You can just set numbers of libraries to be autoloaded when Cygnite
   boots up

    For example -
       Cygnite::loader()->register_classes(
                                            array(
                                                     'CF_Cache' => CF_SYSTEM.'>cygnite>libraries>cache>handler>CF_Cache'.EXT,
                                                     'CF_Authx' => APPVENDORSDIR.'>libs>CF_Authx'.EXT,
                                                     'CF_Common' => APPVENDORSDIR.'>libs>CF_Common'.EXT,
                                          )
    ),


  Above register_classes function allow you to register your libraries dynamically into cygnite engine. You can also check and load core files which is not
  loaded by engine in initial boot up.

  How to Check which classes are registered by Cygnite boot up ?
  ---------------------------------------------------------------------------

    You can check numbers of classes loaded by Cygnite Robot Loader very easily.

    Cygnite::loader()->loaded_classes();

    It will return you all registered classes into robot engine. If you find any core classess are not registered into Cygnite Robotloader then you have a
    option to load and use it dynamically based on your needs register_classess function inside autoload.php file.

    [Note: Class name should be same as file name and Class name should have prefix CF_ in order to register in Cygnite Engine.]

    Register your Models dynamically into Cygnite Robot
    ---------------------------------------------------------------
    But you can autoload your models dynamically which is more efficient with better performance. Multiple models on fly-
    Register all your models in cygnite engine for example -

          Cygnite::loader()->register_models(array(
                                    'Activerecords'=>'apps>models>activerecords',
                                    'Records'=>'apps>models>records'
                    ))


  How to call Model or libraries ?
  --------------------------------
  Calling models and libraries is very easy with cygnite. For example if you want to call sayhello()-
         
           Cygnite::loader()->request('records')->sayhello();


    Output :
    Hellow World !!

  How to autoload helpers  ?
  ---------------------------------------------

   Though Cygnite has option to helpers but we suggest you not to load in initial boot up, because it may
   cause performance issue.

   Cygnite allows you to load core as well as user defined files to load. If you want to load core helpers if not loaded by cygnite engine then
   you can import it simply in configs/autoload.php -

    Cygnite::import('packages>cygnite>helpers>CF_Url');

   And if you would like to load cygnite applications user defined helpers then you can import it as below-

    Cygnite::import('apps>vendors>helpers>CF_General');
