Cygnite Framework User Guide 
============================

   Models
   -------
        Models consists of application data,business logic and functions where you can write your DB related stuffs.
        Model name should be model filename followed by model path name. 
        
        For exxample-
        
        If your model filename is usersmodel.php then your model name should be UsersmodelAppsModels, have a look at
        below example-
        
        <?php
        
        class UsersmodelAppsModels extends CF_ApplicationModel
        {
            function __construct()
            {
               parent::__construct();
            }
            public function getdetails()
            {
                
            }
            
        }    
      ?>
   
   
   How to load and access model functions ?
   ------------------------------------------
        Lets assume your model file name is usersmodel.php. Then you can load your model inside in your controller 
        as bewlow-
        
        <?php
         class WelcomeuserAppsController extends CF_BaseController
         {
           public function __construct()
           {
              parent::__construct();
              // Load in constructor if you want to access it throughout the 
              // controller else load it corresponding method based upon your needs.
              $this->app()->model('usersmodel');
           }
        
           public function action_index()
           {
               $userdetails =  $this->app()->usersmodel->getdetails(); 
               show($userdetails);
           }
           
         }
        
         ?>

    
   How to access model functions in view page ?
   --------------------------------------------
        You can simply call the model in views to fetch data from db as follows -        
        
         
        <html>
        <head>
        <title>Welcome to Cygnite Framewormk</title>
        </head>
        <body>
        <h2></h2>
        
        <div class="content">   
           <h2>Hello World ! </h2> 
           <?php 
                $users = $this->usersmodel->getdetails(); // Call your model functions to fetch data from db
                show($users); // print your data into browser as formated output.           
           ?>
        </div>
        
        </body>     
        </html>
        
        
      These are basics of models. You can find more about Active records and DB queries in Database.md file.
      
      
