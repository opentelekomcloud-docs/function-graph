:original_name: functiongraph_03_0860.html

.. _functiongraph_03_0860:

How Does a Function Obtain the Request Path or Parameters When Using an APIG Trigger?
=====================================================================================

By default, the request path or parameters are included in **event**. A function invokes APIG using its event template. You can obtain the request path or parameters from the function execution result.

Example:

|image1|

-  **queryStringParameters**: parameters following the question mark (?), separated with ampersands (&). These parameters are added in the URL of a GET request, and will be transferred in the URL string format when a GET request is initiated.
-  **path**: API URL.

You can call an API using its request path. Example: **https://464d86ec641d45a683c5919ac57f3823.apig.projectID.com/apig-demo/subpath**

Alternatively, you can call an API by adding request parameters. Example:

https://464d86ec641d45a683c5919ac57f3823.apig.projectID.com/apig-demo\ **/subpath?a=1&b=2**

|image2|

.. |image1| image:: /_static/images/en-us_image_0000001351427305.png
.. |image2| image:: /_static/images/en-us_image_0000001351347601.png
