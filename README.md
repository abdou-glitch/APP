# Device Registry Service

## Usage

All responses will have the form

```json
{
    "data": "Mixed type holding the content of the response",
    "message": "Description of what happened"
}
```

Subsequent response definitions will only detail the expected value of the `data field`

### List all devices

**Definition**

`GET /devices`

**Response**

- `200 OK` on success

```json
[
    {
        "identifier": "Lifx-Lights",
        "name": "Lifx Lights",
        "device_type": "switch",
        "controller_gateway": "10.133.29.93"
    },
    {
        "identifier": "Ble-Beacons",
        "name": "Ble Beacons",
        "device_type": "ble",
        "controller_gateway": "10.133.29.93"
    }
]
```

### Registering a new device

**Definition**

`POST /devices`

**Arguments**

- `"controller_gateway":string` the IP address of the device's controller

If a device with the given identifier already exists, the existing device will be overwritten.

**Response**

- `201 Created` on success

```json
{
   "identifier": "Lifx-Lights",
        "name": "Lifx Lights",
        "device_type": "switch",
        "controller_gateway": "10.133.29.93"
}
```

## Lookup device details

`GET /device/<identifier>`

**Response**

- `404 Not Found` if the device does not exist
- `200 OK` on success

```json
{
  "identifier": "Lifx-Lights",
        "name": "Lifx Lights",
        "device_type": "switch",
        "controller_gateway": "10.133.29.93"
}
```

## Delete a device

**Definition**

`DELETE /devices/<identifier>`

**Response**
