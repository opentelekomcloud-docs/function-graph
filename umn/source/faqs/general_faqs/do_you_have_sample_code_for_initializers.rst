:original_name: functiongraph_03_0882.html

.. _functiongraph_03_0882:

Do You Have Sample Code for Initializers?
=========================================

Yes. See the following examples:

-  Node.js

   .. code-block::

      exports.initializer = function(context, callback) {
          callback(null, '');
          };

-  Python

   .. code-block::

      def my_initializer(context):
          print("hello world!")

-  Java

   .. code-block::

      public void my_initializer(Context context)
      {
      RuntimeLogger log = context.getLogger();
      log.log(String.format("ak:%s", context.getAccessKey()));
      }

-  PHP

   .. code-block::

      <?php
      Function my_initializer($context) {
          echo 'hello world' . PHP_EOL;
          }
      ?>
