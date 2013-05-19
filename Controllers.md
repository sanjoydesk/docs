Cygnite Framework User Guide 
============================

 Controllers
 --------------
 

 i. Controller name should start with upper case and followed by controller path. For example if you have controller 
     as welcomeuser.php and controller path is apps/controllers/welcomeuser.php then your controller name should be
     as- WelcomeuserAppsController.
 ii. Please have two space before starting your controller name and have one tab to start your method name.
 
 

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
















