:original_name: functiongraph_06_0220.html

.. _functiongraph_06_0220:

Response
========

Status Code
-----------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request. For more information, see :ref:`Status Codes <functiongraph_06_1310>`.

For example, if status code 201 is returned for calling the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

:ref:`Figure 1 <functiongraph_06_0220__fig1999718469177>` shows the response header fields for the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__. The **x-subject-token** header field is the desired user token. This token can then be used to authenticate the calling of other APIs.

.. _functiongraph_06_0220__fig1999718469177:

.. figure:: /_static/images/en-us_image_0000001433216038.gif
   :alt: **Figure 1** Header fields of the response to the request for obtaining a user token

   **Figure 1** Header fields of the response to the request for obtaining a user token

Response Body
-------------

The body of a response is often returned in structured format as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__.

.. code-block:: text

   {
       "token": {
           "expires_at": "2019-02-13T06:52:13.855000Z",
           "methods": [
               "password"
           ],
           "catalog": [
               {
                   "endpoints": [
                       {
                           "region_id": "XXXXXXXX",
   ......

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block:: text

   {
     "error_code": "FGS.0111",
     "error_msg": "xxxxxxxxx"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
