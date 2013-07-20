Cygnite Framework User Guide
=========================

  Libraries
  -----------------
  How to work with libraries ?
  ---------------------------------

  Working with libraries are very simple. Cygnite Framework libraries are lazy loaded by internal
  robot loading mechanism. Even Cygnite Framework allows developers to dynamically load libraries
  in autoload file. You can load your user defined libraries which is reside inside your apps directory
  as well as any core library which is not loaded by cygnite.

  Now no need to initialise your libraries. Just use it.

  For example -

  If you want to save details into session using cygnite session library -
  
  You can call the libraries two different way- 

     Cygnite::loader()->Session->save('cygnite','Hellow !! Cygnite you are awesome !');
     
     OR
     
     Cygnite::loader()->Session->save('cygnite','Hellow !! Cygnite you are awesome !');
     

  Similarly you can also retrieve session details -

     echo Cygnite::loader()->Session->retrieve('cygnite');

   Naming Conventions
   --------------------------

    You should follow below naming convention for custom libraries.

  i. Class name and filename should be same.
  ii. Class should have CF_ prefix before your class name.
  iii. First character of the class should be  capitalized.

    For example :

 filename : CF_Common.php

    <?php if ( ! defined('CF_SYSTEM')) exit('External script access not allowed');
     
    class CF_Common
    {
        public function __construct()
        {
          ...
        }
    }

    ?>

   How to auto load custom libraries ?
   ------------------------------------------

   You  can also have your custom libraries inside your apps/vendors/libs/ folder.

   [Note : You should have CF_ prefix in order to use Cygnite robot loader. ]

   For example :

   apps/vendors/libs/CF_Users.php

   You can register this above library as below-

     Cygnite::loader()->register_classes(
                                            array(
                                                     'CF_Users' => APPVENDORSDIR.'>libs>CF_Users'.EXT,
                                          )
                     );

  How to use Cygnite libraries inside custom library ?
  ----------------------------------------------------

   You can use cygnite core libraries as generally you call  - Cygnite::loader()->request('Session')->retrieve('cygnite');

   Access your database object by -
    
    $this->dbname = CF_DBConnector::getInstance($your_database_name);

    Now your can write your pdo queries as generally we write -
        $stmt = $this->dbname->prepare_query('Select username FROM users');   //build user query
        $stmt->execute();
        $users = $stmt->fetchAll(PDO::FETCH_ASSOC);

   That's it all basic information about cygnite framework libraries.
   
