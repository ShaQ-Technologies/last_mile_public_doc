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
POST /passports/import
```

Description: Import excel sheet containing passport data

#### Request Parameters

| Parameter | Type   | Description   |
| :-------- | :----- | :------------ |
| `file`    | `file` | **required**. |

#### Response

200

```json
{
  "message": "Request Successful",
  "data": []
}
```

## Callback Request

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
