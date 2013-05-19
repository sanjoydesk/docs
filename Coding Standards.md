  Cygnite Framework User Guide
==================================

   Introduction
   ------------
    Cygnite Framework is free, open source and user friendly. Mean to say you can actively contribute on cygnite 
    development and it progress. Cygnite source code is currently hosted on Github which provide you easy to fork,
    develop, update and push into our development branch. You can even send me patch to make the framework better.
    My main aim is to provide more user friendly and with almost all feature in single place, which will help any
    web artists.


   Coding Standards
   ---------------------
    There are different coding standards followed by different frameworks. But my idea is to make code clean and bit 
    standard. I have followed some standards in Cygnite Framework which should be maintain by all contributors 
    throughout the framework to make core code structure globally.

   Controllers & Libraries
   -----------------------

   Controllers:
   -------------
    i. Controller name should start with upper case and followed by controller path. For example if you have controller 
      as welcomeuser.php and controller path is apps/controllers/welcomeuser.php then your controller name should be
      as- WelcomeuserAppsController.
    ii. Please have tab before starting your controller name and have two tab to start your method name.
      
      For example -
      <?php
       
       class WelcomeuserAppsController extends CF_BaseController
       {
         public function __construct()
         {
              parent::__construct(); 
         }
        
         public function action_index()
         {
         
         }
         
         public function action_user_details()
         { 
         
         }
       }
     ?>
      
      iii. Method name should be in small letter follows by underscore if needed as above.


   Libraries:
   ----------
     i. All library file name should be added with prefix CF_. for example if your library name is Loader.php than 
       it should have prefix as CF_Loader.php
       <?php
       
        class CF_Loader
        {
          public function load()
          {
             .............
          }
        }
       ?>
     ii. Have proper documentation and comments for your code which will make easy to update the code in future by 
        others if needed.
        
    iii. Method name should be always lowercase and in case of long name underscore should be added.


   Helpers:
   ----------
    i.  Additions of library coding standards helpers file name should have CF_ prefix before filename.
    ii. You can have either CF_ prefix in your helper class name or just name like Url.
    iii. All helpers static methods to access it directly with helper class name.
       
        For Example -
        <?php
            class Url
            {
              public static function redirect_to()
              {
              
              }
              
            }
        ?>
        
    
    Control Structure
    ------------------

    If you have a look at core libraries you can find i have not used any kind of Curly braces if core code. 
    Using curly braces { } is a old fashion of code, so I have almost avoided { } curly braces in my code. 
    My idea is to make code clean and simple to look and maintained same throughout the code.    
    For example- 
    IF / ELSE Conditions
    --------------------  
    <?php    
        if (($conditions1) && ($conditions2)):
              ..............
        elseif ($condition2):
              ...............
        else:
              ................
        endif;
     ?>    
    FOREACH Loop
    ------------  
    <?php    
    foreach ($result_array as $row):
      echo "................";
    endforeach;    
    ?>
    SWITCH CASE Conditions
    ----------------------
    <?php    
    switch ($type):
            case 1:
                  action 1;
            break;
            case 2:
                  action2;
            break;
    endswitch;    
    ?>    
    Ternary Operators:
    ------------------        
    <?php    
    $result = (($conditions1) && ($condtions2)) ? $foo : $bar;    
    ?>
    VARIABLES :
    -----------    
    i. Have your variable name in lowercase with underscore if needed.
    ii. Define the variables before use, don't pass directly into conditions without defining.
    ARRAYS
    -------
    i. Similarly array name should be in lower case and format it as below.
    <?php     
    $result_array = array(
                          'foo'      -> $bar,
                          'name' ->'Sanjoy'
                          );
    ?>    
    
    Documentation and Commenting code:
    ----------------------------------      
    
    Have your code properly documented and with proper comments. Which will be easy for others to update code 
    if needed. Don't use any short tag in your code.Since Cygnite is alpha version you may not find much documentation
    and comments,will be followed in upcoming release.

    Naming Conventions
    ------------------
    Classes
    ---------
    Classes should be given descriptive names. Class name should be begin with upper case and you can either follow
    with underscore for long name else like -      
    <?php    
    class CF_HTML_Tag_Genarator
    {
        ................
    }
    or
    class CF_HTMLTagGenarator
    {
        ..................
    }
      both the case is fine to use.

    Variable and Methods
    ---------------------------

    Private class members are preceded by a single underscore. For example:
    <?php    
        $status_counter        _sortarray()    
    ?>
    Constants should be in UPPERCASE.
    

    Interface name should have prefix as I. If your interface name is "Auth" then It should be like "IAuth". 
    
    
    Try to follow all standards in your code to make cygnite better. Apart from above coding standards you can follow
    pear coding structure for your application except changing core code structure.
    
    
     
    
    
    
