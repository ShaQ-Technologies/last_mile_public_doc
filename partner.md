
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

## Package Statuses

`pending` : Package is yet to be received from Partner

`shipped` : Package has been shipped by Partner

`confirmed` : Customer has been called and delivery confirmed

`received` : Package has been received from Partner

`assigned` : Package has been assigned to a Rider

`in_transit` : Package is in transit to closest warehouse

`dispatched` : Package is en-route to deliver

`not_delivered` : Attempted delivery but couldn't complete it

`rescheduled` : Package delivery rescheduled for new delivery attempt

`delivered` : Package was successfully delivered to customer

`failed` : Package delivery failed multiple times

`return_in_progress` : Package is en-route back to Partner

`returned_to_sender` : Package has been sent back to Partner

`ready_for_pickup` : Package is ready for customer pickup

`customer_hold` : Delivery on hold based on customer request

`customer_unreachable` : Delivery is on hold because customer is unreachable

`suspected_scam` : Delivery is on hold due to suspected scam

`return_home` : Package is being returned to ShaQ Express main warehouse after multiple unsuccessful delivery

## Endpoints

### Login

```http
POST /auth/login
```

Description: Get authentication token for subsequent requests
As a security measure the token is valid for 7 days after which a new one will have to be generated
using the `/auth/login` route.

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
GET /packages?page=1&limit=1
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
                "customerPhone1": "+233244100200",
                "customerPhone2": null,
                "sourceCountry": "Ghana",
                "sourceAddressLine1": "Accra Spintex",
                "sourceAddressLine2": null,
                "destinationCountry": "Ghana",
                "destinationRegion": "Greater Accra",
                "destinationCity": "Accra",
                "destinationAddressLine1": "UPSA Hall, Room 3",
                "destinationAddressLine2": null,
                "destinationPostalCode": null,
                "length": 0,
                "height": 5,
                "weight": 1.2,
                "description": "iPhone 16 pro max black edge silver back casing",
                "labelUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
                "units": 1,
                "type": "box",
                "value": "300.00",
                "handling": "normal",
                "specialInstructions": null,
                "status": "delivered",
                "statusDescription": "Package was successfully delivered to customer",
                "latitude": null,
                "longitude": null,
                "proofPhotoUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
                "dateCreated": "2025-04-10 11:15",
                "items": [
                    {
                        "name" : "iPhone 6",
                        "quantity" : 1,
                    },
                    {
                        "name" : "iPhone 14 Pro",
                        "quantity" : 2,
                    }
                ]
            },
            {
                "partnerRef": "FGVHKJ567",
                "trackingNumber": "20250410X51DIQ",
                "customerName": "Kwaku Ananse",
                "customerPhone1": "+233244100200",
                "customerPhone2": null,
                "sourceCountry": "Ghana",
                "sourceAddressLine1": "Accra Spintex",
                "sourceAddressLine2": null,
                "destinationCountry": "Ghana",
                "destinationRegion": "Greater Accra",
                "destinationCity": "Accra",
                "destinationAddressLine1": "UPSA Hall, Room 3",
                "destinationAddressLine2": null,
                "destinationPostalCode": null,
                "length": 0,
                "height": 5,
                "weight": 1.2,
                "description": "iPhone 16 pro max black edge silver back casing",
                "labelUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
                "units": 1,
                "type": "box",
                "value": "300.00",
                "handling": "normal",
                "specialInstructions": null,
                "status": "pending",
                "statusDescription": "Package is yet to be received from Partner.",
                "latitude": null,
                "longitude": null,
                "proofPhotoUrl": null,
                "dateCreated": "2025-04-10 11:15",
                "items": [
                    {
                        "name" : "iPhone 6",
                        "quantity" : 1,
                    }
                ]
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
        "sourceAddressLine1": "Accra Spintex",
        "sourceAddressLine2": null,
        "destinationCountry": "Ghana",
        "destinationRegion": "Greater Accra",
        "destinationCity": "Accra",
        "destinationAddressLine1": "UPSA Hall, Room 3",
        "destinationAddressLine2": null,
        "destinationPostalCode": null,
        "length": 0,
        "height": 5,
        "weight": 1.2,
        "description": "iPhone 16 pro max black edge silver back casing",
        "labelUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
        "units": 1,
        "type": "box",
        "value": "300.00",
        "handling": "normal",
        "specialInstructions": null,
        "status": "not_delivered",
        "statusDescription": "Attempted delivery but couldn't complete it.",
        "latitude": null,
        "longitude": null,
        "proofPhotoUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
        "dateCreated": "2025-04-10 11:15",
        "items": [
            {
                "name" : "iPhone 6",
                "quantity" : 1,
            },
            {
                "name" : "iPhone 14 Pro",
                "quantity" : 2,
            }
        ],
         "trackingHistory": [
            {
                "name": "not_delivered",
                "description": "Attempted delivery but couldn't complete it.",
                "date": "2025-07-16 09:00",
                "comment": "Customer was unreachable upon arrival. Package rescheduled for 2nd delivery attempt."
            },
            {
                "name": "dispatched",
                "description": "Package is en-route to deliver.",
                "date": "2025-07-15 15:45",
                "comment": null
            },
            {
                "name": "confirmed",
                "description": "Customer has been called and delivery confirmed.",
                "date": "2025-07-15 15:45",
                "comment": null
            },
            {
                "name": "received",
                "description": "Package has been received from Partner.",
                "date": "2025-07-15 15:38",
                "comment": null
            },
            {
                "name": "pending",
                "description": "Package is yet to be received by Partner.",
                "date": "2025-07-14 10:38",
                "comment": null
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
        "partnerRef": "FGVHKJ567",
        "trackingNumber": "20250410X51DIQ",
        "customerName": "Kwaku Ananse",
        "customerPhone1": "+233244100200",
        "customerPhone2": null,
        "sourceCountry": "Ghana",
        "sourceAddressLine1": "Accra Spintex",
        "sourceAddressLine2": null,
        "destinationCountry": "Ghana",
        "destinationRegion": "Greater Accra",
        "destinationCity": "Accra",
        "destinationAddressLine1": "UPSA Hall, Room 3",
        "destinationAddressLine2": null,
        "destinationPostalCode": null,
        "length": 0,
        "height": 5,
        "weight": 1.2,
        "description": "iPhone 16 pro max black edge silver back casing",
        "labelUrl": null,
        "units": 1,
        "type": "box",
        "value": "300.00",
        "handling": "normal",
        "specialInstructions": null,
        "status": "pending",
        "statusDescription": "Package is yet to be received from Partner.",
        "latitude": null,
        "longitude": null,
        "dateCreated": "2025-04-10 11:15",
        "items": [
            {
                "name" : "iPhone 6",
                "quantity" : 1,
            },
            {
                "name" : "iPhone 14 Pro",
                "quantity" : 2,
            }
        ],
         "trackingHistory": [
            {
                "name": "pending",
                "description": "Package is yet to be received by Partner.",
                "date": "2025-07-14 10:38",
                "comment": null
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
        "partnerRef": "12345",
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
        "proofPhotoUrl": null,
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

### Update Package status

```http
POST /packages/{partnerRef}/update-status
```

Description: Update the status of a package

#### Headers

| Parameter       | Type     | Description   |
| :-------------- | :------- | :------------ |
| `Authorization` | `bearer` | **Required**. |

#### Request Parameters

| Parameter                     | Type          | Description                               |
| :---------------------------- | :------------ | :---------------------------------------- |
| `status`                      | `string`      | **required** . in `pending`, `shipped`    |

##### Response

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
        "sourceAddressLine1": "Accra Spintex",
        "sourceAddressLine2": null,
        "destinationCountry": "Ghana",
        "destinationRegion": "Greater Accra",
        "destinationCity": "Accra",
        "destinationAddressLine1": "UPSA Hall, Room 3",
        "destinationAddressLine2": null,
        "destinationPostalCode": null,
        "length": 0,
        "height": 5,
        "weight": 1.2,
        "description": "iPhone 16 pro max black edge silver back casing",
        "labelUrl": "https://debtufr1vwh35.cloudfront.net/labels_test/label/8B73CE6D.png",
        "units": 1,
        "type": "box",
        "value": "300.00",
        "handling": "normal",
        "specialInstructions": null,
        "status": "not_delivered",
        "statusDescription": "Attempted delivery but couldn't complete it.",
        "latitude": null,
        "longitude": null,
        "dateCreated": "2025-04-10 11:15",
        "items": [
            {
                "name" : "iPhone 6",
                "quantity" : 1,
            },
            {
                "name" : "iPhone 14 Pro",
                "quantity" : 2,
            }
        ],
         "trackingHistory": [
            {
                "name": "not_delivered",
                "description": "Attempted delivery but couldn't complete it.",
                "date": "2025-07-16 09:00",
                "comment": "Customer was unreachable upon arrival. Package rescheduled for 2nd delivery attempt."
            },
            {
                "name": "dispatched",
                "description": "Package is en-route to deliver.",
                "date": "2025-07-15 15:45",
                "comment": null
            },
            {
                "name": "confirmed",
                "description": "Customer has been called and delivery confirmed.",
                "date": "2025-07-15 15:45",
                "comment": null
            },
            {
                "name": "received",
                "description": "Package has been received from Partner.",
                "date": "2025-07-15 15:38",
                "comment": null
            },
            {
                "name": "pending",
                "description": "Package is yet to be received by Partner.",
                "date": "2025-07-14 10:38",
                "comment": null
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
