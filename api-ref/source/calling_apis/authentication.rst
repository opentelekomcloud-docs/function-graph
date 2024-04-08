:original_name: functiongraph_06_0230.html

.. _functiongraph_06_0230:

Authentication
==============

Requests for calling an API can be authenticated using either of the following methods:

-  Token-based authentication: Requests are authenticated using a token.
-  AK/SK-based authentication: Requests are authenticated by encrypting the request body using an AK/SK.

Token-based Authentication
--------------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the Identity and Access Management (IAM) API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API.

In :ref:`Making an API Request <functiongraph_06_0210>`, the process of calling the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__ is described. After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when other APIs are called. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:
