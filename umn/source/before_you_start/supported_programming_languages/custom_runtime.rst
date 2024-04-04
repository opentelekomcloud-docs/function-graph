:original_name: functiongraph_01_0406.html

.. _functiongraph_01_0406:

Custom Runtime
==============

Scenarios
---------

A runtime runs the code of a function, reads the handler name from an environment variable, and reads invocation events from the runtime APIs of FunctionGraph. The runtime passes event data to the function handler and returns the response from the handler to FunctionGraph.

FunctionGraph supports custom runtimes. You can use an executable file named **bootstrap** to include a runtime in your function deployment package. The runtime runs the function's handler method when the function is invoked.

Your runtime runs in the FunctionGraph execution environment. It can be a shell script or a binary executable file that is compiled in Linux.

.. note::

   After programming, simply package your code into a ZIP file (Java, Node.js, Python, and Go) or JAR file (Java), and upload the file to FunctionGraph for execution. When creating a ZIP file, place the handler file under the **root** directory to ensure that your code can run normally after being decompressed.

   If you edit code in Go, zip the compiled file, and ensure that the name of the dynamic library file is consistent with the plug-in name of the handler. For example, if the name of the dynamic library file is **testplugin.so**, set the handler name to **testplugin.Handler**.

Runtime File bootstrap
----------------------

If there is a file named **bootstrap** in your function deployment package, FunctionGraph executes that file. If the **bootstrap** file is not found or not executable, your function will return an error when invoked.

The runtime code is responsible for completing initialization tasks. It processes invocation events in a loop until it is terminated.

The initialization tasks run once for each instance of the function to prepare the environment for handling invocations.

Runtime APIs
------------

FunctionGraph provides HTTP runtime APIs to receive function invocation events and returns response data in the execution environment.

-  **Obtaining Invocation Event**

   **Method** - Get

   **Path** - http://$RUNTIME_API_ADDR/v1/runtime/invocation/request

   This API is used to retrieve an invocation event. The response body contains the event data. The following table describes additional data about the invocation contained in the response header.

   .. _functiongraph_01_0406__en-us_topic_0000001298786845_table9387122910529:

   .. table:: **Table 1** Response header information

      +----------------------+--------------------------------------------------------------------------------------------------------+
      | Parameter            | Description                                                                                            |
      +======================+========================================================================================================+
      | X-Cff-Request-Id     | Request ID.                                                                                            |
      +----------------------+--------------------------------------------------------------------------------------------------------+
      | X-CFF-Access-Key     | AK of the account. An agency must be configured for the function if this variable is used.             |
      +----------------------+--------------------------------------------------------------------------------------------------------+
      | X-CFF-Auth-Token     | Token of the account. An agency must be configured for the function if this variable is used.          |
      +----------------------+--------------------------------------------------------------------------------------------------------+
      | X-CFF-Invoke-Type    | Invocation type of the function.                                                                       |
      +----------------------+--------------------------------------------------------------------------------------------------------+
      | X-CFF-Secret-Key     | SK of the account. An agency must be configured for the function if this variable is used.             |
      +----------------------+--------------------------------------------------------------------------------------------------------+
      | X-CFF-Security-Token | Security token of the account. An agency must be configured for the function if this variable is used. |
      +----------------------+--------------------------------------------------------------------------------------------------------+

-  **Invocation Response**

   **Method** - POST

   **Path** - http://$RUNTIME_API_ADDR/v1/runtime/invocation/response/$REQUEST_ID

   This API is used to send a successful invocation response to FunctionGraph. After the runtime invokes the function handler, it publishes the response from the function to the invocation response path.

-  **Invocation Error**

   **Method** - POST

   **Path** - http://$RUNTIME_API_ADDR/v1/runtime/invocation/error/$REQUEST_ID

   **$REQUEST_ID** is the value of variable **X-Cff-Request-Id** in the header of an event retrieval response. For more information, see :ref:`Table 1 <functiongraph_01_0406__en-us_topic_0000001298786845_table9387122910529>`.

   **$RUNTIME_API_ADDR** is a system environment variable. For more information, see :ref:`Table 2 <functiongraph_01_0406__en-us_topic_0000001298786845_table11731825111317>`.

   This API is used to send an error invocation response to FunctionGraph. After the runtime invokes the function handler, it publishes the response from the function to the invocation response path.

Runtime Environment Variables
-----------------------------

You can use both custom and runtime environment variables in function code. The following table lists the runtime environment variables that are used in the FunctionGraph execution environment.

.. _functiongraph_01_0406__en-us_topic_0000001298786845_table11731825111317:

.. table:: **Table 2** Environment variables

   ==================== ================================================
   Key                  Description
   ==================== ================================================
   RUNTIME_PROJECT_ID   Project ID
   RUNTIME_FUNC_NAME    Function name
   RUNTIME_FUNC_VERSION Function version
   RUNTIME_PACKAGE      App to which the function belongs
   RUNTIME_HANDLER      Function handler
   RUNTIME_TIMEOUT      Function timeout duration
   RUNTIME_USERDATA     Value passed through an environment variable
   RUNTIME_CPU          Number of allocated CPU cores
   RUNTIME_MEMORY       Allocated memory
   RUNTIME_CODE_ROOT    Directory that stores the function code
   RUNTIME_API_ADDR     Host IP address and port of a custom runtime API
   ==================== ================================================

The value of a custom environment variable can be retrieved in the same way as the value of a FunctionGraph environment variable.

Example
-------

This example contains one file called **bootstrap**. The file is implemented in Bash.

The runtime loads the function script from the deployment package by using two variables.

The **bootstrap** file is as follows:

.. code-block::

   #!/bin/sh
   set -o pipefail
   #Processing requests loop
   while true
   do
   HEADERS="$(mktemp)"
     # Get an event
     EVENT_DATA=$(curl -sS -LD "$HEADERS" -X GET "http://$RUNTIME_API_ADDR/v1/runtime/invocation/request")
     # Get request id from response header
     REQUEST_ID=$(grep -Fi x-cff-request-id "$HEADERS" | tr -d '[:space:]' | cut -d: -f2)
     if [ -z "$REQUEST_ID" ]; then
       continue
     fi
     # Process request data
     RESPONSE="Echoing request: hello world!"
     # Put response
     curl -X POST "http://$RUNTIME_API_ADDR/v1/runtime/invocation/response/$REQUEST_ID" -d "$RESPONSE"
   done

After loading the script, the runtime processes invocation events in a loop until it is terminated. It uses the API to retrieve invocation events from FunctionGraph, passes the events to the handler, and then sends responses back to FunctionGraph.

To obtain the request ID, the runtime saves the API response header in a temporary file, and then reads the request ID from the **x-cff-request-id** header field. The runtime processes the retrieved event data and sends a response back to FunctionGraph.

The following is an example of source code in Go. It can be executed only after compilation.

.. code-block:: text

   package main

   import (
       "bytes"
       "encoding/json"
       "fmt"
       "io"
       "io/ioutil"
       "log"
       "net"
       "net/http"
       "os"
       "strings"
       "time"
   )

   var (
       getRequestUrl           = os.ExpandEnv("http://${RUNTIME_API_ADDR}/v1/runtime/invocation/request")
       putResponseUrl          = os.ExpandEnv("http://${RUNTIME_API_ADDR}/v1/runtime/invocation/response/{REQUEST_ID}")
       putErrorResponseUrl     = os.ExpandEnv("http://${RUNTIME_API_ADDR}/v1/runtime/invocation/error/{REQUEST_ID}")
       requestIdInvalidError   = fmt.Errorf("request id invalid")
       noRequestAvailableError = fmt.Errorf("no request available")
       putResponseFailedError  = fmt.Errorf("put response failed")
       functionPackage         = os.Getenv("RUNTIME_PACKAGE")
       functionName            = os.Getenv("RUNTIME_FUNC_NAME")
       functionVersion         = os.Getenv("RUNTIME_FUNC_VERSION")

       client = http.Client{
           Transport: &http.Transport{
               DialContext: (&net.Dialer{
                   Timeout: 3 * time.Second,
               }).DialContext,
           },
       }
   )

   func main() {
       // main loop for processing requests.
       for {
           requestId, header, payload, err := getRequest()
           if err != nil {
               time.Sleep(50 * time.Millisecond)
               continue
           }

           result, err := processRequestEvent(requestId, header, payload)
           err = putResponse(requestId, result, err)
           if err != nil {
               log.Printf("put response failed, err: %s.", err.Error())
           }
       }
   }

   // event processing function
   func processRequestEvent(requestId string, header http.Header, evtBytes []byte) ([]byte, error) {
       log.Printf("processing request '%s'.", requestId)
       result := fmt.Sprintf("function: %s:%s:%s, request id: %s, headers: %+v, payload: %s", functionPackage, functionName,
           functionVersion, requestId, header, string(evtBytes))

       var event FunctionEvent
       err := json.Unmarshal(evtBytes, &event)
       if err != nil {
           return (&ErrorMessage{ErrorType: "invalid event", ErrorMessage: "invalid json formated event"}).toJsonBytes(), err
       }

       return (&APIGFormatResult{StatusCode: 200, Body: result}).toJsonBytes(), nil
   }

   func getRequest() (string, http.Header, []byte, error) {
       resp, err := client.Get(getRequestUrl)
       if err != nil {
           log.Printf("get request error, err: %s.", err.Error())
           return "", nil, nil, err
       }
       defer resp.Body.Close()

       // get request id from response header
       requestId := resp.Header.Get("X-CFF-Request-Id")
       if requestId == "" {
           log.Printf("request id not found.")
           return "", nil, nil, requestIdInvalidError
       }

       payload, err := ioutil.ReadAll(resp.Body)
       if err != nil {
           log.Printf("read request body error, err: %s.", err.Error())
           return "", nil, nil, err
       }

       if resp.StatusCode != 200 {
           log.Printf("get request failed, status: %d, message: %s.", resp.StatusCode, string(payload))
           return "", nil, nil, noRequestAvailableError
       }

       log.Printf("get request ok.")
       return requestId, resp.Header, payload, nil
   }

   func putResponse(requestId string, payload []byte, err error) error {
       var body io.Reader
       if payload != nil && len(payload) > 0 {
           body = bytes.NewBuffer(payload)
       }

       url := ""
       if err == nil {
           url = strings.Replace(putResponseUrl, "{REQUEST_ID}", requestId, -1)
       } else {
           url = strings.Replace(putErrorResponseUrl, "{REQUEST_ID}", requestId, -1)
       }

       resp, err := client.Post(strings.Replace(url, "{REQUEST_ID}", requestId, -1), "", body)
       if err != nil {
           log.Printf("put response error, err: %s.", err.Error())
           return err
       }
       defer resp.Body.Close()

       responsePayload, err := ioutil.ReadAll(resp.Body)
       if err != nil {
           log.Printf("read request body error, err: %s.", err.Error())
           return err
       }

       if resp.StatusCode != 200 {
           log.Printf("put response failed, status: %d, message: %s.", resp.StatusCode, string(responsePayload))
           return putResponseFailedError
       }

       return nil
   }

   type FunctionEvent struct {
       Type string `json:"type"`
       Name string `json:"name"`
   }

   type APIGFormatResult struct {
       StatusCode      int               `json:"statusCode"`
       IsBase64Encoded bool              `json:"isBase64Encoded"`
       Headers         map[string]string `json:"headers,omitempty"`
       Body            string            `json:"body,omitempty"`
   }

   func (result *APIGFormatResult) toJsonBytes() []byte {
       data, err := json.MarshalIndent(result, "", "  ")
       if err != nil {
           return nil
       }

       return data
   }

   type ErrorMessage struct {
       ErrorType     string `json:"errorType"`
       ErrorMessage  string `json:"errorMessage"`
   }

   func (errMsg *ErrorMessage) toJsonBytes() []byte {
       data, err := json.MarshalIndent(errMsg, "", "  ")
       if err != nil {
           return nil
       }

       return data
   }

:ref:`Table 3 <functiongraph_01_0406__en-us_topic_0000001298786845_table122572411113>` describes the environment variables used in the preceding code.

.. _functiongraph_01_0406__en-us_topic_0000001298786845_table122572411113:

.. table:: **Table 3** Environment variables

   ==================== =================================
   Environment Variable Description
   ==================== =================================
   RUNTIME_FUNC_NAME    Function name
   RUNTIME_FUNC_VERSION Function version
   RUNTIME_PACKAGE      App to which the function belongs
   ==================== =================================
