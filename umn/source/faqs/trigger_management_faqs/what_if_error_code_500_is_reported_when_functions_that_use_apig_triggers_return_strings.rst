:original_name: functiongraph_03_0290.html

.. _functiongraph_03_0290:

What If Error Code 500 Is Reported When Functions that Use APIG Triggers Return Strings?
========================================================================================

Ensure that the function response for an invocation by API Gateway has been encapsulated and contains **body(String)**, **statusCode(int)**, **headers(Map)**, and **isBase64Encoded(boolean)**.

The following is an example response returned by a Node.js function that uses an APIG trigger:

.. code-block:: text

   exports.handler = function (event, context, callback) {
       const response = {
           'statusCode': 200,
           'isBase64Encoded': false,
           'headers': {
               "Content-type": "application/json"
           },
           'body': 'Hello, FunctionGraph with APIG',
       }
       callback(null, response);
   }

The following is an example response returned by a Java function that uses an APIG trigger:

.. code-block:: text

   import java.util.Map;

   public HttpTriggerResponse index(String event, Context context){
           String body = "<html><title>FunctionStage</title>"
                   + "<h1>This is a simple APIG trigger test</h1><br>"
                   + "<h2>This is a simple APIG trigger test</h2><br>"
                   + "<h3>This is a simple APIG trigger test</h3>"
                   + "</html>";
           int code = 200;
           boolean isBase64 = false;
           Map<String, String> headers = new HashMap<String, String>();
           headers.put("Content-Type", "text/html; charset=utf-8");
           return new HttpTriggerResponse(body, headers, code, isBase64);
       }


   class HttpTriggerResponse {
       private String body;
       private Map<String, String> headers;
       private int statusCode;
       private boolean isBase64Encoded;
       public HttpTriggerResponse(String body, Map<String,String> headers, int statusCode, boolean isBase64Encoded){
           this.body = body;
           this.headers = headers;
           this.statusCode = statusCode;
           this.isBase64Encoded = isBase64Encoded;
       }
   }
