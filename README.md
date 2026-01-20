# Proto-files

## Compiling Protocol Buffers

Protocol buffers (or Protobuf) are a method of serializing the data that can be transmitted between microservices, applications or used in communication between IoT devices and servers. Protocol Buffers have the same function as well known and widely used JSON and XML. Like JSON and XML, the Protobufs are language-neutral and platform-neutral. Moreover, Protobuf is optimised to be fast and use as little network bandwidth as possible by minimizing the size of transmitted data. This makes Protobuf a perfect choice for serializing the data sent by the battery powered IoT devices.

  

Unlike JSON and XML, the data and context are separated in Protobuf. Context is defined in the configuration files called proto files (.proto). These files contain field names along with their types and identifiers (eg. string first_name = 1; string surname = 2;), based on the configuration fields Protobuf data is being serialized. The proto files can be compiled to generate code in the user’s selected programming language – a class with setters and getters for all the fields defined in the proto file. Currently, Google provides a code generator for multiple languages including C++, C#, Dart, Go, Java and Python under an open source license.

  

In order to compile the proto file to a Python class, you will require a protobuf compiler. If you don’t have the compiler yet, download the compiler from its official Github repository: [https://github.com/protocolbuffers/protobuf/releases](https://github.com/protocolbuffers/protobuf/releases). You need to download the compiler dedicated for the operating system you are using (eg. for Windows download [protoc-21.12-win64.zip](https://github.com/protocolbuffers/protobuf/releases/download/v21.12/protoc-21.12-win64.zip) and unzip it)

  

Once you have the protbuf compiler, download the proto files, unzip the folder and place the files in the same directory as the protobuf compiler (if you are using Windows .../protoc-21.12-win64/bin/). Run the protocol buffer compiler protoc on your .proto files - open a terminal window and enter:

  

    protoc --python_out=.. proto_measurement_types.proto
    protoc --python_out=.. proto_measurements.proto
    protoc --python_out=.. proto_config_types.proto
    protoc --python_out=.. proto_config_rule.proto
    protoc --python_out=.. proto_config.proto
    protoc --python_out=.. proto_extended_configuration.proto
    protoc --python_out=.. proto_device_info.proto
    
# Changelog - Protobuf Refactoring in version 07.xx

## Description
This update focuses on refactoring field names across several `.proto` files to improve naming consistency, clarity, and alignment with the current system domain. 

> [!IMPORTANT]
> **Wire Compatibility:** **Fully Preserved.** > All field tags (numeric identifiers) remain unchanged. Legacy devices and services using the old field names in their source code will continue to communicate successfully with services using the new definitions at the binary level.

## Technical Notes
* **Breaking Change (Source Level):** This refactoring requires updates to the application logic. After regenerating the stubs, you must update all references to getters, setters, and builders.
* **Import Statements:** The file `proto_rule.proto` has been renamed to `proto_config_rule.proto`. Ensure all import statements in your project are updated.

---

## Detailed Mapping of Changes

### File Rename
| Old Filename | New Filename |
| :--- | :--- |
| `proto_rule.proto` | `proto_config_rule.proto` |

### Field Name Changes
| Message / Context | Old Field Name | New Field Name |
| :--- | :--- | :--- |
| **ProtoMeasurements** | `serial_num` | `serial_number` |
| **ProtoMeasurements** | `hash` | `configuration_hash` |
| **ProtoMeasurements** | `signal` | `signal_strength` |
| **ProtoDeviceInfo** | `serial_num` | `serial_number` |
| **ProtoRuntime** | `min_battery_voltage` | `battery_voltage` |
| **ProtoConfig** | `hash` | `configuration_hash` |
| **ProtoConfig** | `hash_timestamp` | `configuration_hash_timestamp` |
| **ProtoConfig** | `errors` | `configuration_errors` |
| **ProtoConfig** | `error_timestamp` | `configuration_error_timestamp` |
| **ProtoConfig** | `accept_without_testing` | `accept_without_testing_request` |
| **ProtoConfig** | `request_configuration` | `configuration_request` |
| **ProtoConfig** | `request_device_info` | `device_info_request` |
| **ProtoConfig** | `request_fw_update` | `update_software_request` |
| **ProtoConfig** | `request_runtime_errors_clear` | `clear_runtime_errors_request` |
| **ProtoConfig** | `modem_update_request` | `update_modem_request` |
| **ProtoConfig** | `memory_reset_request` | `reset_memory_request` |
| **ProtoConfig** | `output_control_state_request` | `set_output_control_state_request` |
| **ProtoConfig** | `apn_user_name` | `apn_username` |
