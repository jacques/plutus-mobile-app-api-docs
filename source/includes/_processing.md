# Processing Endpoints

These endpoints are for the Azure Microservices and uses a seperate API key to the users mobile apps.

## Upload a Document (customer)

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/processing/users/d19bff36-4733-11e5-946b-9ba904d8238e/documents"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"document_type":"1',"file_hash":"","url":"https://imgdocs.blob.core.windows.net/docs/shrek.jpg?sv=2017-11-09&ss=bqtf&srt=sco&sp=rwdlacup&se=2018-11-13T18:23:21Z&sig=ozX6jU0OROIirHvxGXOP0xqEpPt3P1bBYdUXknuq41g%3D&_=1542104774928"}'
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": {
    "uuid": "895b2fcc-545f-11e7-8279-67635886d357",
    "document_type": 1,
    "file_name": "55af7356-2641-11e6-9641-51a94b3cc203 - POID - GOVID - Vin Diesel.pdf",
    "file_hash": "4f9ef9c744b05f339b4d74c83a5e98c361ab8a7c35f95532e0ec977e71bfd321",
    "file_size": 3718903,
    "created_at": "2017-06-01 15:33:20"
  }
}
```

This endpoint allows for uploading (getting the platform to download the file from
Azure Blob Store) of documents from the Azure Microservice once the file has been
processed after being uploaded from the mobile phone and resized.

### HTTP Request

`POST https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/documents`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user who you want to upload a document for

### POST Parameters

Parameter | Type | Description
--------- | ---- | -----------
document_type | integer | Indicates the type of document.  See <a href="#document-types">Document Types</a> below.

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the document
document_type | integer | Indicates the type of document.  See <a href="#document-types">Document Types</a> below.
file_name | string (255) | File name including a random uuid at the front of the file name
file_hash | string (255) | sha256 of the uploaded file
file_size | integer | Size of the uploaded file
created_at | datetime | Datetime in GMT that the file was uploaded

