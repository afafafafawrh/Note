###  Create HttpClient

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

