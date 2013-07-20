    Cygnite Framework Database User Guide
    =================================

    What Database Driver Cygnite Supports ?
    -------------------------------------------------
    Though we have option of connecting multiple database driver but cygnite framework is in development stage
     it's currently supports mysql alone and we are updating with lots of new features to fulfill your needs in simple way.
    Soon we will bring most of the leading database driver available for you.

    Features of Cygnite Database Model Classes ?
    -------------------------------------------------------

    We used pdo for database connection and queries. Which provides you more features with better security on your database queries.

    Beyond simplicity of the Cygnite, its allow you to generate queries in one or two lines of code. No more worries to write queries
    Cygnite Mysql adapter will generate all queries based on your needs. With all these Cygnite allows you to write raw queries.

    -------------------------------------------------------------
    A. Select Command Builder of Cygnite Framework :
    ---------------------------------------------------------------

    How to fetch data from Database ?
    ------------------------------------------

    Now data access is simple more simpler then  you think. You can fetch data from your tables in single line of code.
    If you provide your database name in database configuration it will act as database layer object to retrieve data
    from database.

    For example -

    If your database name is cygnite given in database configuration page i.e database.php.


    First activate your class to build your query and select values from table.The following function allow you to build SQL Select statement.
     -----------------------------------------------------------------------------------------------------------------------------------------------------

    class Users extends CF_BaseModel
    {
            public function __construct()
            {
                    parent::__construct('cygnite'); //Provide your database name here to connect
            }

            public function get_users_details()
            {
                   //Method Chaining to make compact code
                  return $this->select('username,password,userid')
                                      ->where('name','Sanjay','=')
                                     ->group_by(array('name'))
                                    ->order_by('id','DESC')
                                   ->limit(3)
                                  ->fetch_all('guestbook');
            }

     }

    -------------------------------------------------------------------------------------------------------------------------------------------------------

    By default above function retrieve results as assoc array. You can retrieve results in different types. Just type as second parameter as follows-

<<<<<<< master
    $data =  $this->select('username,password,userid')->fetch_all('users',FETCH_BOTH);

    and FETCH_CLASS,FETCH_GROUP,FETCH_OBJECT,FETCH_COLUMN etc.

    Finally you need to flush result to release resources.

    $this->flushresult();

    How to get row count ?
   ---------------------------
    You can get number of rows selected by our query builder. Just use -

    $this->num_row_count();

    How to write where condition ?
    -------------------------------------
    Query builder give you provision to have single or multiple where condition in a single line.

    For Example:
   If you want to pass a single condition then you can call -

   $this->where('username','Sanjoy Dey');

    Which will act like - Select `username`,`password` from `users` where `username` = 'Sanjoy Dey'

    If you want to pass multiple conditions into where then you can just form an array and pass into where directly as follows-

    $where = array(
                              'name =' => 'Sanjoy',
                              'id >'=> '4'
                               );

    $this->where($where);

    The above query will generate multiple where conditions as below-

    Select `username`,`password` from `users` where `username` = 'Sanjoy' AND `id ` > 4;

    Similarly you can pass like, or, not, in, between etc. into the where array.

    For example -
        $where = array(
                              'name LIKE' => '%Sanjoy%',
                              'id <'=> '4'
                               );

      [Note: Limitation - Don't pass a single conditions into array format. It will give unknown result.]

      How to write group by conditions ?
      -----------------------------------------
     You can pass single as well as multiple group by condition into cygnite query builder.

     For example -

     $this->group_by('name');
     OR
     $this->group_by(array('name','comment'));

     Above function will generate-

    i. Select `username`,`password` from `users` where `username` = 'Sanjoy' AND `id ` > 4 GROUP BY `name`;
    ii. Select `username`,`password` from `users` where `username` = 'Sanjoy' AND `id ` > 4 GROUP BY `name`,`comment`;

    How do I write ORDER By condition ?
    --------------------------------------------
    You can just pass parameters to order_by function to generate follows-

      $this->order_by('id','DESC');

      Which will generate - ORDER BY `id` DESC

      How to Limit records ?
      --------------------------
      You can fetch records from database and limit the numbers of records into UI.

     $this->limit(3);
     OR
     $this->limit(0,3);

     Which will generate - LIMIT 0,3

     --------------------------------------------------------------------------------------------------------------------------------------------------------------------
     Now lets show how cygnite make your work clean and simple. All together You can Just have a single line of code to fetch from database
     which looks very compact and simple.

     $data = array();
    $data =$this->where($where)->group_by(array('name','comment'))->order_by('id','DESC')->limit(2)->select('name,comment')->fetch_all('guestbook');

    Finally don't forget to flush your queries as I mentioned before.
    --------------------------------------------------------------------------------------------------------------------------------------------------------------------

    How to debug Queries ?
    ----------------------------
    After executing query you if you want to check your query you can just call -


   $this->debug_query();

    -------------------------------------------------------------
    B. Insert Command Builder by Cygnite Framework :
    -------------------------------------------------------------

    How to insert datas into Database ?
    ------------------------------------------
    Cygnite makes your work very simpler. Now you can insert batch arrays into your table on the go.

    Form an array and pass into insert function, that's all Cygnite will take care of rest.

    For example-

          $this->name = "Cygnite Active Records !!";
         $this->entry_date = date('Y-m-d H:m:s');
         $this->comment = 'Insert query http://www.cygniteframework.com';
         $this->save('guestbook');

    That's it. You can debug query to see what query build by our query builder.


     -------------------------------------------------------------
    B. Update Command Builder by Cygnite Framework :
    -------------------------------------------------------------

    How to update datas into Database ?
    ---------------------------------------------

    Update command builder also simpler as insert function.

       $this->name = "Cygnite Active Records Update Query";
        $this->entry_date = date('Y-m-d H:m:s');
        $this->comment = 'Update query http://www.cygniteframework.com';
        $this->save('guestbook',array('id'=> 27));

     -------------------------------------------------------------
    B. Delete Command Builder by Cygnite Framework :
    -------------------------------------------------------------

    How to delete rows from Database ?
    ---------------------------------------------

        $this->id = 26;
        $this->remove('guestbook');

    ------------------------------
   C. Building Raw Queries :
   ------------------------------

    How to write raw queries ?
    --------------------------------
    Have a full access on your database and write your own queries and build it as like below.

      $data = array();

     $query = $this->prepare_query("SELECT name,comment FROM `guestbook` WHERE `name` = 'Sanjay' GROUP BY `name`,`comment` ORDER BY id DESC");

     $data = $query->fetchAll(PDO::FETCH_CLASS);

   ----------------------------------------------------
   D. Building Your Own Queries With Binding:
   -----------------------------------------------------
    Since we are using PDO for database access, Cygnite allow you to write PDO queries with Binding and execute queries in more secure way.



    Hope Cygnite query builder will help you to minimize your code and visit back to have a new additional features into Cygnite core
    database layer.
