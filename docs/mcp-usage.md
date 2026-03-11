# MCP Protocol IoT Control Usage Guide

> This document describes how to implement IoT control for ESP32 devices based on the MCP protocol. For detailed protocol flow, please refer to [`mcp-protocol.md`](./mcp-protocol.md).

## Introduction

MCP (Model Context Protocol) is the new generation protocol recommended for IoT control. It discovers and invokes "Tools" between the backend and devices through the standard JSON-RPC 2.0 format, enabling flexible device control.

## Typical Usage Flow

1. After device startup, it establishes a connection with the backend through the base protocol (such as WebSocket/MQTT).
2. The backend initializes the session through the MCP protocol's `initialize` method.
3. The backend retrieves all tools (features) and parameter descriptions supported by the device via `tools/list`.
4. The backend calls specific tools via `tools/call` to control the device.

For detailed protocol format and interaction, see [`mcp-protocol.md`](./mcp-protocol.md).

## Device-Side Tool Registration Method

Devices register "tools" that can be called by the backend through the `McpServer::AddTool` method. The commonly used function signature is as follows:

```cpp
void AddTool(
    const std::string& name,           // Tool name, should be unique and hierarchical, e.g., self.dog.forward
    const std::string& description,    // Tool description, concisely explains the function for LLM understanding
    const PropertyList& properties,    // Input parameter list (can be empty), supported types: boolean, integer, string
    std::function<ReturnValue(const PropertyList&)> callback // Callback implementation when the tool is called
);
```
- name: Unique identifier for the tool, recommended to use "module.function" naming style.
- description: Natural language description for AI/user understanding.
- properties: Parameter list, supported types include boolean, integer, string, with configurable ranges and default values.
- callback: Actual execution logic when a call request is received, return value can be bool/int/string.

## Typical Registration Example (using ESP-Hi as example)

```cpp
void InitializeTools() {
    auto& mcp_server = McpServer::GetInstance();
    // Example 1: No parameters, control robot to move forward
    mcp_server.AddTool("self.dog.forward", "Move robot forward", PropertyList(), [this](const PropertyList&) -> ReturnValue {
        servo_dog_ctrl_send(DOG_STATE_FORWARD, NULL);
        return true;
    });
    // Example 2: With parameters, set light RGB color
    mcp_server.AddTool("self.light.set_rgb", "Set RGB color", PropertyList({
        Property("r", kPropertyTypeInteger, 0, 255),
        Property("g", kPropertyTypeInteger, 0, 255),
        Property("b", kPropertyTypeInteger, 0, 255)
    }), [this](const PropertyList& properties) -> ReturnValue {
        int r = properties["r"].value<int>();
        int g = properties["g"].value<int>();
        int b = properties["b"].value<int>();
        led_on_ = true;
        SetLedColor(r, g, b);
        return true;
    });
}
```

## Common Tool Call JSON-RPC Examples

### 1. Get Tool List
```json
{
  "jsonrpc": "2.0",
  "method": "tools/list",
  "params": { "cursor": "" },
  "id": 1
}
```

### 2. Control Chassis Forward
```json
{
  "jsonrpc": "2.0",
  "method": "tools/call",
  "params": {
    "name": "self.chassis.go_forward",
    "arguments": {}
  },
  "id": 2
}
```

### 3. Switch Light Mode
```json
{
  "jsonrpc": "2.0",
  "method": "tools/call",
  "params": {
    "name": "self.chassis.switch_light_mode",
    "arguments": { "light_mode": 3 }
  },
  "id": 3
}
```

### 4. Flip Camera
```json
{
  "jsonrpc": "2.0",
  "method": "tools/call",
  "params": {
    "name": "self.camera.set_camera_flipped",
    "arguments": {}
  },
  "id": 4
}
```

## Notes
- Tool names, parameters, and return values should follow the device-side `AddTool` registration.
- It is recommended that all new projects uniformly adopt the MCP protocol for IoT control.
- For detailed protocol and advanced usage, please refer to [`mcp-protocol.md`](./mcp-protocol.md).