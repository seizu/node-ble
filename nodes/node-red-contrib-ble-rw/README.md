# node-red-contrib-ble-rw

A Node-RED node for Bluetooth Low Energy (BLE) read, write and notify operations, based on the `node-ble` library.

## Features
- **Hybrid Configuration**: Set MAC, Handle, and Operation in the node settings or override them via `msg.payload`.
- **Auto-Retry**: Configurable retry attempts and delay for connection errors.
- **Three Outputs**: 
  1. `stdout`: Success confirmation.
  2. `stderr`: Error messages.
  3. `return`: Raw hex data from read or notify operations.

## Operations

| Operation | Description |
|---|---|
| `read` | Read value from handle |
| `write` | Write hex data to handle |
| `subscribe_once` | Enable notify, receive first notification, auto-unsubscribe |
| `subscribe` | Enable notify, forward every notification to output 3 |
| `unsubscribe` | Disable notify and disconnect |

## Input Payload Format
You can trigger the node by sending a JSON object:
```json
{
    "operation": "write",
    "handle": "0x0074",
    "mac": "D8:71:4D:00:6D:3D",
    "data": "10000000"
}
```

## Node Settings

| Setting | Description | Default |
|---|---|---|
| MAC Address | BLE device MAC address | - |
| Handle | GATT handle (hex, e.g. `0x002C`) | - |
| Operation | Default operation | `read` |
| Max Retries | Connection retry attempts | `3` |
| Retry Delay | Delay between retries in ms | `2000` |

## Installation

```bash
npm install node-red-contrib-ble-rw
```

## Requirements
- Node-RED
- `node-ble` library
- Linux with BlueZ (e.g. Raspberry Pi)