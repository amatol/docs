---
editable: false
---

# Method listVersions
Retrieves the list of versions for the specified function, or of all function versions
in the specified folder.
 

 
## HTTP request {#https-request}
```
GET https://serverless-functions.api.cloud.yandex.net/functions/v1/versions
```
 
## Query parameters {#query_params}
 
Parameter | Description
--- | ---
folderId | ID of the folder to list function versions for. To get a folder ID make a [list](/docs/resource-manager/api-ref/Folder/list) request.
functionId | ID of the function to list versions for. To get a function ID use a [list](/docs/functions/functions/api-ref/Function/list) request.
pageSize | The maximum number of results per page to return. If the number of available results is larger than `pageSize`, the service returns a [nextPageToken](/docs/functions/functions/api-ref/Function/listVersions#responses) that can be used to get the next page of results in subsequent list requests.  Default value: 100.  Acceptable values are 0 to 1000, inclusive.
pageToken | Page token. To get the next page of results, set `pageToken` to the [nextPageToken](/docs/functions/functions/api-ref/Function/listVersions#responses) returned by a previous list request.  The maximum string length in characters is 100.
filter | A filter expression that filters resources listed in the response.  The expression must specify: 1. The field name. Currently filtering can only be applied to the [Function.name](/docs/functions/functions/api-ref/Function#representation) field. 2. A conditional operator. Can be either `=` or `!=` for single values, `IN` or `NOT IN` for lists of values. 3. The value. Must be 3-63 characters long and match the regular expression `^[a-z][-a-z0-9]{1,61}[a-z0-9]$`. Example of a filter: `name=my-function`.  The maximum string length in characters is 1000.
 
## Response {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "versions": [
    {
      "id": "string",
      "functionId": "string",
      "description": "string",
      "createdAt": "string",
      "runtime": "string",
      "entrypoint": "string",
      "resources": {
        "memory": "string"
      },
      "executionTimeout": "string",
      "serviceAccountId": "string",
      "imageSize": "string",
      "status": "string",
      "tags": [
        "string"
      ],
      "logGroupId": "string",
      "environment": "object"
    }
  ],
  "nextPageToken": "string"
}
```

 
Field | Description
--- | ---
versions[] | **object**<br><p>Version of a function. For details about the concept, see <a href="/docs/functions/concepts/function#version">Function versions</a>.</p> 
versions[].<br>id | **string**<br><p>ID of the version.</p> 
versions[].<br>functionId | **string**<br><p>ID of the function that the version belongs to.</p> 
versions[].<br>description | **string**<br><p>Description of the version.</p> <p>The string length in characters must be 0-256.</p> 
versions[].<br>createdAt | **string** (date-time)<br><p>Creation timestamp for the version.</p> <p>String in <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a> text format.</p> 
versions[].<br>runtime | **string**<br><p>ID of the runtime environment for the function.</p> <p>Supported environments and their identifiers are listed in the <a href="/docs/functions/concepts/runtime">Runtime environments</a>.</p> 
versions[].<br>entrypoint | **string**<br><p>Entrypoint for the function: the name of the function to be called as the handler.</p> <p>Specified in the format <code>&lt;function file name&gt;.&lt;handler name&gt;</code>, for example, <code>index.myFunction</code>.</p> 
versions[].<br>resources | **object**<br><p>Resources allocated to the version.</p> <p>Resources allocated to a version.</p> 
versions[].<br>resources.<br>memory | **string** (int64)<br><p>Amount of memory available to the version, specified in bytes.</p> <p>Acceptable values are 33554432 to 1073741824, inclusive.</p> 
versions[].<br>executionTimeout | **string**<br><p>Timeout for the execution of the version.</p> <p>If the timeout is exceeded, Cloud Functions responds with a 504 HTTP code.</p> 
versions[].<br>serviceAccountId | **string**<br><p>ID of the service account associated with the version.</p> 
versions[].<br>imageSize | **string** (int64)<br><p>Final size of the deployment package after unpacking.</p> 
versions[].<br>status | **string**<br><p>Status of the version.</p> <ul> <li>CREATING: Version is being created.</li> <li>ACTIVE: Version is ready to use.</li> </ul> 
versions[].<br>tags[] | **string**<br><p>Version tags. For details, see <a href="/docs/functions/concepts/function#tag">Version tag</a>.</p> 
versions[].<br>logGroupId | **string**<br><p>ID of the log group for the version.</p> 
versions[].<br>environment | **object**<br><p>Environment settings for the version.</p> 
nextPageToken | **string**<br><p>Token for getting the next page of the list. If the number of results is greater than the specified <a href="/docs/functions/functions/api-ref/Function/listVersions#query_params">pageSize</a>, use <code>nextPageToken</code> as the value for the <a href="/docs/functions/functions/api-ref/Function/listVersions#query_params">pageToken</a> parameter in the next list request.</p> <p>Each subsequent page will have its own <code>nextPageToken</code> to continue paging through the results.</p> 