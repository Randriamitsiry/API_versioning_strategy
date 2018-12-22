# API Versioning
API may have many version. So, what about all products that use previous version of the API?
There are some way to manage this such as :

  - URL versionning
  - Accept headers versioning
  - Hostname versioning
  - Query param versionning
# NOTICE:
For every approach, you have to define a logic in you action of handling each request for:

   - If version doesn't exists?
   - If action is not defined
The best way is to define a default action to handle this. For example, you have an interface wich contain all disponible version of the API. If version is not specified by client, you just return default action

Default action may be an exception that notice the client that the API version he wants to call is not disponible or just return a defaults return values

### Let's talk about them all one by one !

## URL VERSIONING
Suppose your API has versions like: v1, v2, v3. With URL VERSIONING, your request will be like
```
GET /v1/action/ HTTP/1.1
Host: host.com
Accept: application/json
```
The advantage with this approach is that URL is more signifiant and more easy to maintain
### BUT!, 
If you have not yet think about versioning your API before and you had an url like host/api?, previous url style will not be able to handle this. This is not the best solution for your case

## ACCEPT HEADERS VERSIONING
In many case, API and consumers use JSON or XML to exchange data. This approach use request param to specify what version of the API client want to consume as the request accept PARAM. 
For example:
```
GET /api/ HTTP/1.1
Host: host.com
Accept: application/details.json; version=1.0
```
## HOSTNAME VERSIONING
This approach need that you have to create subdomain for each version of the API.
we don't refers to action name for this approach but by the API version subdomain.
```
GET /api/ HTTP/1.1
Host: v1.host.com
Accept: application/json
```
## QUERY PARAM VERSIONING

Client just need to pass wich version of the API he want  to consumes like : 
```
GET /api/?version=v1 HTTP/1.1
Host: host.com
Accept: application/json
```
