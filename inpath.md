# General

Api documentation for ShaQ Express Partners Passport Delivery integration with Central Delivery System (InPath)

|              |                                               |
| :----------- | :-------------------------------------------- |
| version      | 1.0                                           |
| Dev Base Url | `https://test-partner.shaqexpress.com/api/v1` |

## Headers

| Header       | Type               |
| :----------- | :----------------- |
| Content-Type | `application/json` |
| Accept       | `application/json` |

## Endpoints

### Create Passports

```http
POST /passports/create
```

Description: Create passports for shipment

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Request Parameters

| Parameter                        | Type     | Description   |
| :------------------------------- | :------- | :------------ |
| `passports`                      | `array`  | **required**. |
| `passports.*.batch_number`       | `string` | **required**. |
| `passports.*.application_id`     | `string` | **required**. |
| `passports.*.application_type`   | `string` | **required**. |
| `passports.*.application_center` | `string` | **required**. |
| `passports.*.issued_date`        | `string` | **required**. |
| `passports.*.surname`            | `string` | **required**. |
| `passports.*.firstname`          | `string` | **required**. |
| `passports.*.othernames`         | `string` | **optional**. |
| `passports.*.phone`              | `string` | **required**. |
| `passports.*.email`              | `string` | **required**. |
| `passports.*.city`               | `string` | **required**. |
| `passports.*.suburb`             | `string` | **optional**. |
| `passports.*.street`             | `string` | **required**. |
| `passports.*.postal_address`     | `string` | **optional**. |
| `passports.*.digital_address`    | `string` | **optional**. |
| `passports.*.reference`          | `string` | **optional**. |
| `passports.*.national_id`        | `string` | **optional**. |

##### Response

200

```json
{
  "message": "Passports created successfully",
  "data": null
}
```

### Get Passport Details

```http
GET /passports/:application_id
```

Description: Get passport details

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

##### Response

200

```json
{
    "message": "Request successful",
    "data": {
        "batchNumber": "304F77G234556",
        "applicationId": "25RXR2QTQPU6D96",
        "applicationType": "Regular32",
        "issuedDate": "2024-01-15T00:00:00.000Z",
        "customerName": "Kwame Mensah",
        "phone": "+233244123456/+233549632604",
        "city": "Accra",
        "street": "Liberation Road, House No. 23",
        "suburb": "East Legon",
        "postalAddress": "P.O. Box 1234, Accra",
        "reference": "REF-2024-001",
        "nationalId": "GHA-123456789-0",
        "status": "received",
        "statusDescription": "Package has been received from Partner",
        "statusMap": "RCV",
        "dateCreated": "2025-11-26 14:22",
        "trackingHistory": [
            {
                "name": "pending",
                "description": "Package is yet to be received by Partner",
                "date": "2025-11-26 14:25",
                "comment": null
            }
        ]
    }
}
```
