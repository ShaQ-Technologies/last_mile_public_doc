
# General

Api documentation for ShaQ Express Partners Last Delivery

|          |                                                    |
| :------- | :------------------------------------------------- |
| version  | 1.0                                                |
| Dev Base Url | `https://test-partner.shaqexpress.com/api/v1`  |

## Headers

| Header       | Type               |
| :----------- | :----------------- |
| Content-Type | `application/json` |
| Accept       | `application/json` |

## Endpoints

### Login

```http
POST /auth/login
```

Description: Get authentication token for subsequent requests

#### Request Parameters

| Parameter     | Type     | Description   |
| :-----------  | :------- | :------------ |
| `identifier`  | `string` | **required**. |
| `secret`      | `string` | **required**. |

#### Response

200

```json
{
    "message": "Request successful",
    "data": {
        "token": "UtXdU9HODhjdmtTNkRtUWNsVlM4OWI1d2Z2TXVIanlkRk"
    }
}
```

### Get Packages

```http
GET /packages
```

Description: Get all packages

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Response

200

```json
{
    "message": "Request successful",
    "data": {
        "list": [
            {
                "partnerRef": "FGVHKJ567",
                "trackingNumber": "20250410X51DIQ",
                "customerName": "Kwaku Ananse",
                "customerPhone1": "+233266100200",
                "customerPhone2": "+233255100200",
                "sourceCountry": "Ghana",
                "sourceAddressLine1": "Accra",
                "sourceAddressLine2": "East Legon",
                "destinationCountry": "Ghana",
                "destinationRegion": "Greater Accra",
                "destinationCity": "Accra",
                "destinationAddressLine1": "UPSA Hall, Room 3",
                "destinationAddressLine2": "",
                "destinationPostalCode": null,
                "length": 31,
                "height": 20,
                "weight": 3,
                "description": "iPhone 16 pro max black edge silver back casing",
                "units": 1,
                "type": "box",
                "value": 5000,
                "items": [
                    {
                        "name" : "iPhone 6",
                        "quantity" : 1,
                    }
                ],
                "handling": "normal",
                "specialInstructions": null,
                "hasLabel": true,
                "status": "pending",
                "statusDescription": "Package is yet to be received from Partner.",
                "latitude": "1.3000000",
                "longitude": "-4.3400000",
                "dateCreated": "2025-04-10 07:13"
            }
        ],
        "meta": {
            "total": 1,
            "perPage": 15,
            "currentPage": 1,
            "lastPage": 1
        }
    }
}
```

### Get single Package

```http
GET /packages/{partnerRef}
```

Description: Get package details

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Response

200

```json
{
    "message": "Request successful",
    "data": {
        "partnerRef": "FGVHKJ567",
        "trackingNumber": "20250410X51DIQ",
        "customerName": "Kwaku Ananse",
        "customerPhone1": "+233244100200",
        "customerPhone2": null,
        "sourceCountry": "Ghana",
        "sourceAddressLine1": "Accra",
        "sourceAddressLine2": "East Legon",
        "destinationCountry": "Ghana",
        "destinationRegion": "Greater Accra",
        "destinationCity": "Accra",
        "destinationAddressLine1": "UPSA Hall, Room 3",
        "destinationAddressLine2": "",
        "destinationPostalCode": null,
        "length": 31,
        "height": 20,
        "weight": 3,
        "description": "iPhone 16 pro max black edge silver back casing",
        "units": 1,
        "type": "box",
        "value": 5000,
        "items": [
            {
                "name" : "iPhone 6",
                "quantity" : 1,
            }
        ],
        "handling": "normal",
        "specialInstructions": null,
        "hasLabel": true,
        "status": "pending",
        "statusDescription": "Package is yet to be received from Partner.",
        "latitude": null,
        "longitude": null,
        "dateCreated": "2025-04-10 11:15",
        "trackingHistory": [
            {
                "name": "processing",
                "description": "Package is being sorted, scanned, and prepared for dispatch",
                "date": "2025-04-11 12:00"
            },
            {
                "name": "received",
                "description": "Package received from Partner",
                "date": "2025-04-11 09:10"
            },
            {
                "name": "pending",
                "description": "Package is yet to be received from Partner.",
                "date": "2025-04-10 11:15"
            }
        ]
    }
}
```

### Delete pending Package

```http
DELETE /packages/{partnerRef}
```

Description: Delete a package. Only pending packages can be deleted

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Response

200

```json
{
    "message": "Package deleted",
    "data": null
}
```

### Create Package

```http
POST /packages
```

Description: Create a package for shipment

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Request Parameters

| Parameter                     | Type          | Description                                       |
| :---------------------------- | :------------ | :------------------------------------------------ |
| `partner_ref`                 | `string`      | **required**.                                     |
| `customer_name`               | `string`      | **required**.                                     |
| `customer_phone_1`            | `string`      | **required**.                                     |
| `customer_phone_2`            | `string`      | **optional**.                                     |
| `source_country_iso2`         | `string`      | **required**.                                     |
| `source_address_line_1`       | `string`      | **required**.                                     |
| `source_address_line_2`       | `string`      | **optional**.                                     |
| `destination_country_iso2`    | `string`      | **required**.                                     |
| `destination_region`          | `string`      | **required if `region_id` is empty**.             |
| `destination_city`            | `string`      | **required**.                                     |
| `destination_address_line_1`  | `string`      | **required**.                                     |
| `destination_address_line_2`  | `string`      | **optional**.                                     |
| `destination_postal_code`     | `string`      | **optional**.                                     |
| `length`                      | `decimal`     | **optional**.                                     |
| `height`                      | `decimal`     | **optional**.                                     |
| `weight`                      | `decimal`     | **optional**.                                     |
| `description`                 | `string`      | **required**.                                     |
| `units`                       | `string`      | **required**.                                     |
| `type`                        | `string`      | **required** . in `parcel`, `box`                 |
| `handling`                    | `string`      | **required** . in `normal`, `fragile`             |
| `special_instructions`        | `string`      | **optional**.                                     |
| `latitude`                    | `decimal`     | **optional**.                                     |
| `longitude`                   | `decimal`     | **optional**.                                     |
| `value`                       | `decimal`     | **required**.                                     |
| `items`                       | `array`       | **required**. {name, quantity}                    |
| `include_label`               | `boolean`     | **optional**.   default `false`                   |
| `region_id`                   | `integer`     | **required if `destination_region` is empty**.    |

##### Response

200

```json
{
    "message": "Package created successfully",
    "data": {
        "id": 1,
        "partnerRef": "ASFWERTG",
        "trackingNumber": "30A19BCC",
        "customerName": "Najib Alhassan",
        "customerPhone1": "0244100200",
        "customerPhone2": null,
        "sourceCountry": "Ghana",
        "sourceAddressLine1": "Accra, Ghana",
        "sourceAddressLine2": null,
        "destinationCountry": "Ghana",
        "destinationRegion": "Western",
        "destinationCity": "Madina",
        "destinationAddressLine1": "Jerusalem Street, Old Road",
        "destinationAddressLine2": null,
        "destinationPostalCode": null,
        "length": 3,
        "height": 1,
        "weight": 0.4,
        "description": "Lorem Ipsum",
        "units": 1,
        "type": "parcel",
        "handling": "fragile",
        "specialInstructions": null,
        "hasLabel": false,
        "status": "pending",
        "statusDescription": "Package is yet to be processed by Partner.",
        "latitude": null,
        "longitude": null,
        "landmark": null,
        "region": {
            "id": 2,
            "name": "Western"
        },
        "rider": null,
        "dateCreated": "2025-06-05 11:11",
        "trackingHistory": [
            {
                "name": "pending",
                "description": "Package is yet to be processed by Partner.",
                "date": "2025-06-05 11:11"
            }
        ]
    }
}
```

### Update a Package

```http
PATCH /packages/{partnerRef}
```

Description: Update a specific package

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Request Parameters

| Parameter                     | Type          | Description                           |
| :---------------------------- | :------------ | :------------------------------------ |
| `customer_name`               | `string`      | **optional**.                         |
| `customer_phone_1`            | `string`      | **optional**.                         |
| `customer_phone_2`            | `string`      | **optional**.                         |
| `source_country_iso2`         | `string`      | **optional**.                         |
| `source_address_line_1`       | `string`      | **optional**.                         |
| `source_address_line_2`       | `string`      | **optional**.                         |
| `destination_country_iso2`    | `string`      | **optional**.                         |
| `destination_region`          | `string`      | **optional**.                         |
| `destination_city`            | `string`      | **optional**.                         |
| `destination_address_line_1`  | `string`      | **optional**.                         |
| `destination_address_line_2`  | `string`      | **optional**.                         |
| `destination_postal_code`     | `string`      | **optional**.                         |
| `length`                      | `decimal`     | **optional**.                         |
| `height`                      | `decimal`     | **optional**.                         |
| `weight`                      | `decimal`     | **optional**.                         |
| `description`                 | `string`      | **optional**.                         |
| `units`                       | `string`      | **optional**.                         |
| `type`                        | `string`      | **optional** . in `parcel`, `box`     |
| `handling`                    | `string`      | **optional** . in `normal`, `fragile` |
| `special_instructions`        | `string`      | **optional**.                         |
| `latitude`                    | `decimal`     | **optional**.                         |
| `longitude`                   | `decimal`     | **optional**.                         |
| `value`                       | `decimal`     | **optional**.                         |
| `items`                       | `array`       | **optional**. {name, quantity}        |
| `include_label`               | `boolean`     | **optional**.                         |

##### Response

200

```json
{
    "message": "Request successful",
    "data": {
        "partnerRef": "TEMU567",
        "trackingNumber": "20250410X51DIQ",
        "customerName": "Kwaku Ananse",
        "customerPhone1": "+233266100200",
        "customerPhone2": "+233255100200",
        "sourceCountry": "China",
        "sourceAddressLine1": "Beijing",
        "sourceAddressLine2": "Hana Province 14th street",
        "destinationCountry": "Ghana",
        "destinationRegion": "Ashanti",
        "destinationCity": "Kumasi",
        "destinationAddressLine1": "knust",
        "destinationAddressLine2": "katanga room 4",
        "length": 31,
        "height": 20,
        "weight": 3,
        "description": "Samsing 16 pro max black edge silver back casing",
        "units": 1,
        "type": "box",
        "handling": "normal",
        "hasLabel": true,
        "status": "pending",
        "statusDescription": "Package is yet to be received from Partner.",
        "latitude": 1.3,
        "longitude": -4.34,
        "dateCreated": "2025-04-10 07:13",
        "trackingHistory": [
            {
                "name": "pending",
                "description": "Package is yet to be received from Partner.",
                "date": "2025-04-10 07:13"
            }
        ]
    }
}
```

### Track Package

```http
GET /tracking/{trackingNumber}
```

Description: Get tracking statuses of a specific package

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Response

200

```json
{
    "message": "Package tracking",
    "data": {
        "description": "Kitchen cabinet",
        "status": "shipped",
        "statusDescription": "Package has been shipped by Partner.",
        "tracking": [
            {
                "status": "shipped",
                "description": "Package has been shipped by Partner.",
                "date": "2025-04-10 15:17"
            },
            {
                "status": "pending",
                "description": "Package is yet to be shipped by Partner.",
                "date": "2025-04-10 15:16"
            },
            {
                "status": "shipped",
                "description": "Package has been shipped by Partner.",
                "date": "2025-04-10 15:15"
            },
            {
                "status": "shipped",
                "description": "Package has been shipped by Partner.",
                "date": "2025-04-10 15:15"
            },
            {
                "status": "pending",
                "description": "Package is yet to be shipped by Partner.",
                "date": "2025-04-10 15:14"
            }
        ]
    }
}
```

### Get Regions

```http
GET /setup/regions
```

Description: Get all allowable regions

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Response

200

```json
{
    "message": "Request successful",
    "data": [
        {
            "id": 16,
            "name": "Western North"
        },
        {
            "id": 15,
            "name": "Ashanti"
        },
    ]
}
```
