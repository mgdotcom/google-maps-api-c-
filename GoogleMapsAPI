using System;
using System.Net.Http;
using System.Threading.Tasks;
using Newtonsoft.Json;

public class GoogleMapsAPI
{
    private const string API_URL = "https://maps.googleapis.com/maps/api/geocode/json?address=";
    private readonly HttpClient _client;

    public GoogleMapsAPI()
    {
        _client = new HttpClient();
    }

    public async Task<string> GetAddress(double latitude, double longitude)
    {
        var url = $"{API_URL}{latitude},{longitude}";
        var response = await _client.GetAsync(url);
        var json = await response.Content.ReadAsStringAsync();
        var result = JsonConvert.DeserializeObject<dynamic>(json);
        return result.results[0].formatted_address;
    }
}
