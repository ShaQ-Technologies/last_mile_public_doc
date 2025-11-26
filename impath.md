# General

Api documentation for ShaQ Express Partners Last Delivery

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
        "id": 7540,
        "partnerRef": "25KQK5JMJIN9W29",
        "trackingNumber": "2A48376C",
        "customerName": "Kwaku Ananse",
        "customerPhone1": "+233208765432",
        "customerPhone2": null,
        "sourceCountry": "Ghana",
        "sourceAddressLine1": "No. 5 Agostinho Neto Rd, Liberation Avenue, Airport Residential Area, Accra, Ghana",
        "sourceAddressLine2": null,
        "destinationCountry": "Ghana",
        "destinationRegion": "Greater Accra",
        "destinationCity": "Tema",
        "destinationAddressLine1": "Meridian Road, Block 12",
        "destinationAddressLine2": null,
        "destinationPostalCode": null,
        "length": 0,
        "height": 0,
        "weight": 0,
        "description": null,
        "labelUrl": null,
        "units": 1,
        "type": "parcel",
        "handling": "fragile",
        "specialInstructions": null,
        "hasLabel": false,
        "status": "pending",
        "statusDescription": "Package is yet to be received by Partner",
        "latitude": null,
        "longitude": null,
        "landmark": "",
        "newRegion": null,
        "rider": null,
        "proofPhotoUrl": null,
        "partner": "MOFA",
        "assignedCompany": null,
        "items": [
            {
                "name": "Passport",
                "quantity": 1
            }
        ],
        "scheduleDate": "2025-11-26 14:22",
        "deliveryFee": "0.00",
        "value": "0.00",
        "date": "2025-11-26 14:25",
        "isCompleted": false,
        "hasChangedLocation": false,
        "trackingHistory": [
            {
                "name": "pending",
                "description": "Package is yet to be received by Partner",
                "comment": null,
                "date": "2025-11-26T14:25:07.000+00:00"
            },
        ]
    }
}
```
