Cygnite Framework User Guide
============================


  Helper : Profiler
  -------------------

  How to benchmark your applications ?
  ---------------------------------------------

  Cygnite Framework allow you to benchmark your application with profiler helper. Now
  knowing code execution time and memory consumption is so simple, with cygnite.

  Start benchmarking -
  -----------------------
   To start profiling you can simply write

    Profiler::start('block1');

  to start your profiler. Start your profiler before writing your custom code and once you completed
  you have to end the profiler with same starting point key.
 For example-

   Profiler::end('block1');

  How to have multiple profiling block in same application code ?
  ---------------------------------------------------------------------------

    You also can have multiple profiling block but be sure you are closing correctly profiler block.
    For example-

    Profiler::start('block1');
    Profiler::start('block2');
    ............................................
    Your custom code goes here
    .............................................
    Profiler::end('block2');
    Profiler::end('block1');


