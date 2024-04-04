:original_name: functiongraph_03_0350.html

.. _functiongraph_03_0350:

How Can I Speed Up Initial Access to a Function?
================================================

C# and Go support a lower startup speed than other languages due to mechanism issues. You can use the following methods to speed up initial access to a function:

-  Allocate more memory to the function.

-  Simplify function code, for example, delete unnecessary dependency packages.

-  When using C# in non-concurrent scenarios, you can also:

   Create a one-minute timer trigger to ensure that there is at least one active instance.
