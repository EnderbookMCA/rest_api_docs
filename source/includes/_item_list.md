# Item List

```ruby
require "uri"
require "net/http"

url = URI("http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```python
# Using Requests
import requests

url = "http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

# Using http.client
import http.client

conn = http.client.HTTPSConnection("localhost", 3000)
payload = ''
headers = {}
conn.request("GET", "/api/v1/items.json?minecraft_version=1.12.2", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

```shell
curl --location --request GET 'http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2'
```

```java
// Using Unirest
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.get("http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2")
  .asString();

// Using OkHttp
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2")
  .method("GET", null)
  .build();
Response response = client.newCall(request).execute();
```

```javascript
// Using Fetch
var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

fetch("http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));

// Using jQuery
var settings = {
  "url": "http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2",
  "method": "GET",
  "timeout": 0,
};

$.ajax(settings).done(function (response) {
  console.log(response);
});

// Using XHR
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://localhost:3000/api/v1/items.json?minecraft_version=1.12.2");

xhr.send();
```

> The above command returns JSON structured like this:

```json
"status": 200,
"data": [
    {
        "type": 0,
        "meta": 0,
        "name": "Air",
        "text_type": "air",
        "image_format": "png"
    }//, several hundred more items after this.
]
```

This endpoint retrieves all item data possibilities for Minecraft version 1.12.2 and earlier. It's a big, honkin' file, so be ready for a massive payload. This endpoint is intended for you to familiarize yourself with how an Item is structured when building Kit and Ender Chest archive create requests.

### HTTP Request

`GET https://enderbook.com/api/v1/items.json?minecraft_version=1.12.2`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
minecraft_version | 1.12.2 | Support for other versions soon, hopefully!
