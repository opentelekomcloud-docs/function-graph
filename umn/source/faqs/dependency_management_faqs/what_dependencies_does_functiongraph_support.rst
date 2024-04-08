:original_name: functiongraph_03_0886.html

.. _functiongraph_03_0886:

What Dependencies Does FunctionGraph Support?
=============================================

**Supported Dependencies**

FunctionGraph supports standard libraries and third-party dependencies.

-  Standard libraries

   When using standard libraries, you can import them to your inline code, or package and upload them to FunctionGraph.

-  Supported non-standard libraries

   FunctionGraph provides built-in third-party components, as described in :ref:`Table 1 <functiongraph_03_0886__table143351951242>` and :ref:`Table 2 <functiongraph_03_0886__table39721459145614>`. You can import these components to your inline code in the same way as you import standard libraries.

   .. _functiongraph_03_0886__table143351951242:

   .. table:: **Table 1** Third-party components integrated with the Node.js runtime

      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Name            | Description                                                                                                                                                                                                                                            | Version |
      +=================+========================================================================================================================================================================================================================================================+=========+
      | q               | Asynchronous method encapsulation                                                                                                                                                                                                                      | 1.5.1   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | co              | Asynchronous process control                                                                                                                                                                                                                           | 4.6.0   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | lodash          | Common tool and method library                                                                                                                                                                                                                         | 4.17.10 |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | esdk-obs-nodejs | OBS sdk                                                                                                                                                                                                                                                | 2.1.5   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | express         | Simplified web-based application development framework                                                                                                                                                                                                 | 4.16.4  |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | fgs-express     | Provides a Node.js application framework for FunctionGraph and APIG to run serverless applications and REST APIs. This component provides an example of using the Express framework to build serverless web applications or services and RESTful APIs. | 1.0.1   |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | request         | Simplifies HTTP invocation and supports HTTPS and redirection.                                                                                                                                                                                         | 2.88.0  |
      +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+

   .. _functiongraph_03_0886__table39721459145614:

   .. table:: **Table 2** Non-standard libraries supported by the Python runtime

      ========= ======================== =======
      Module    Description              Version
      ========= ======================== =======
      dateutil  Date and time processing 2.6.0
      requests  HTTP library             2.7.0
      httplib2  httpclient               0.10.3
      numpy     Mathematical computation 1.13.1
      redis     Redis client             2.10.5
      obsclient OBS client               ``-``
      smnsdk    SMN access               1.0.1
      ========= ======================== =======

-  Other third-party libraries

   For other third-party libraries not listed in the preceding tables, package and upload them to an OBS bucket or on the function details page. For details, see :ref:`How Do I Create a Dependency on the FunctionGraph Console? <functiongraph_03_0888>` These libraries will then be used in your function code.
