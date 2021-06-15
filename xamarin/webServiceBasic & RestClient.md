#  Create HttpClient

```c#
HttpClient _client = new HttpClient();
```

client.GetAsync

```c#
HttpResponseMessage response = await _client.GetAsync(uri);
```

Check Response

```c#
List<Repository> repositories = null;
if (response.IsSuccessStatusCode){
	string content = await response.Content.ReadAsStringAsync();
    repositories = JsonConvert.DeserializeObject<List<Repository>>(content);
}
-----------
try{
 response.EnsureSuccessStatusCode(); // if IsSuccessStatusCode is false throw exception

}
catch(HttpRequestException e)
{
     
}
```

Match the data name with the Repository class using [JsonProperty("(value)")]

## Example 1 Post

```c#
var url = "url"
var parameters = Newtonsoft.Json.JsonConvert.SerializeObject(new
{
    field1 = "",
    field2= ""
});

HttpResponseMessage response;

using (var httpClient = new HttpClient())
{

    httpClient.DefaultRequestHeaders.Accept.Add(new System.Net.Http.Headers.MediaTypeWithQualityHeaderValue("application/json"));

    response = await httpClient.PostAsync(url, new StringContent(parameters, Encoding.UTF8, "application/json"));
}

var data = await response.Content.ReadAsStringAsync();
```



# RestClient

```C#
private static string host = "url";

var client = new RestClient(host);            
var request = new RestRequest(Method.POST); // Method.Get Method.Put...

request.AddParameter("field1", value);
request.AddParameter("field2", value);  // same as Example 1
s
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);

```

