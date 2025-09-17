# General

Api documentation for ShaQ Express Partners Last Delivery

|              |     |
| :----------- | :-- |
| version      | 1.0 |
| Dev Base Url |     |

## Headers

| Header       | Type               |
| :----------- | :----------------- |
| Content-Type | `application/json` |
| Accept       | `application/json` |

## Endpoints

### Passport Import

```http
POST /passports/upload-manifest
```

Description: Import excel sheet containing passport data

#### Request Parameters

| Parameter | Type   | Description   |
| :-------- | :----- | :------------ |
| `file`    | `file` | **required**. |

#### Expected Excel Columns Structure
 - batch_reference
 - application_id
 - application_type
 - application_center
 - passport_number
 - issued_date
 - surname
 - firstname
 - othernames
 - phone
 - email
 - city
 - suburb
 - street
 - postal_address
 - digital_address
 - referenc_id
 - national_id

 >Note: Columns should be structured in the order listed with no heading


#### Response

200

```json
{
  "message": "Request Successful",
  "data": []
}
```

## Callback Requests

### Import Update

```http
POST /your-callback-url
```

Description: A request sent to the callback URL when an import is successful and when an import is received

#### Request Parameters

| Parameter          | Type     |
| :----------------- | :------- |
| `event`            | `string` |
| `import_reference` | `string` |
| `status`           | `string` |

#### Import Status Events
 - import/successful
 - import/received

### Passport Update

```http
POST /your-callback-url
```

Description: A request sent to the callback URL when a passsport status is updated

#### Request Parameters

| Parameter          | Type     |
| :----------------- | :------- |
| `event`            | `string` |
| `passport_number`  | `string` |
| `status`           | `string` |

#### Import Status Events
 - passport/confirmed
 - passport/dispatched
 - passport/delivered
