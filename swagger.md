# Bill pay application for XYZ corporation
This is API design of bill pay application for XYZ corporation

## Version: 1.0.11

**License:** [Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

[Find out more about Swagger](http://swagger.io)
### /register

#### POST
##### Summary:

Resgister new customer

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | 200 response |
| 400 |  |
| 429 |  |
| 500 |  |

### /balance/{emailId}

#### GET
##### Summary:

Get balance

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| emailId | path |  | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 | 200 response |
| 400 |  |
| 429 |  |
| 500 |  |
