:original_name: functiongraph_06_0260.html

.. _functiongraph_06_0260:

Obtaining a Project ID
======================

Obtaining a Project ID on the Console
-------------------------------------

When calling APIs, you need to enter a project ID in some URLs. To obtain a project ID, perform the following steps:

#. Log in to the management console.

#. Click the username and choose **My Credentials** from the drop-down list.

   On the **My Credentials** page, view the project ID.

Obtaining a Project ID by Calling an API
----------------------------------------

A project ID can also be obtained by calling a specific API. For details, see `Querying Project Information <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/project_management/querying_project_information_based_on_the_specified_criteria.html#en-us-topic-0057845625>`__.

The API used to obtain a project ID is **GET https://**\ *{Endpoint}*\ **/v3/projects**, where *{Endpoint}* indicates the IAM endpoint. You can obtain the IAM endpoint from `Regions and Endpoints <https://docs.otc.t-systems.com/additional/endpoints.html>`__. For details on API calling authentication, see :ref:`Authentication <functiongraph_06_0230>`.

The following is an example response. The value of **id** in the **projects** section is the project ID.

.. code-block:: text

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "xxx",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }
