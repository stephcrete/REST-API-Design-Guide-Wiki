A good example of this is report generation.

Let's suppose that we have a "reports" resource that we can interact with the request the creation of reports. Some reports might be delivered directly, others might require a lot of time to be generated.

Here's how the exchange might go:
```
1) First request
POST /reports
{
    "type": "monthly",
    "periodStart": "2015-01-01",
    "periodEnd": "2016-01-01"
}
 
2) First response
202 Accepted
Location: /reports/<uuid>
 
3) Second request
GET /reports/<uuid>
 
4) Second response
202 Accepted
{
    "status": "BUSY"
}
 
5) Third request (a while later)
200 OK
{
    // data
}
```