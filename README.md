# Proto-files

## Compiling Protocol Buffers

Protocol buffers (or Protobuf) are a method of serializing the data that can be transmitted between microservices, applications or used in communication between IoT devices and servers. Protocol Buffers have the same function as well known and widely used JSON and XML. Like JSON and XML, the Protobufs are language-neutral and platform-neutral. Moreover, Protobuf is optimised to be fast and use as little network bandwidth as possible by minimizing the size of transmitted data. This makes Protobuf a perfect choice for serializing the data sent by the battery powered IoT devices.

  

Unlike JSON and XML, the data and context are separated in Protobuf. Context is defined in the configuration files called proto files (.proto). These files contain field names along with their types and identifiers (eg. string first_name = 1; string surname = 2;), based on the configuration fields Protobuf data is being serialized. The proto files can be compiled to generate code in the user’s selected programming language – a class with setters and getters for all the fields defined in the proto file. Currently, Google provides a code generator for multiple languages including C++, C#, Dart, Go, Java and Python under an open source license.

  

In order to compile the proto file to a Python class, you will require a protobuf compiler. If you don’t have the compiler yet, download the compiler from its official Github repository: [https://github.com/protocolbuffers/protobuf/releases/tag/v3.17.1](https://github.com/protocolbuffers/protobuf/releases/tag/v3.17.1). You need to download the compiler dedicated for the operating system you are using (eg. for Windows download [protoc-3.17.1-win64.zip](https://github.com/protocolbuffers/protobuf/releases/download/v3.17.1/protoc-3.17.1-win64.zip) and unzip it)

  

Once you have the protbuf compiler, download the proto files, unzip the folder and place the files in the same directory as the protobuf compiler (if you are using Windows .../protoc-3.17.1-win64/bin/). Run the protocol buffer compiler protoc on your .proto files - open a terminal window and enter:

  

    protoc --python_out=.. proto_measurement_types.proto
    protoc --python_out=.. proto_measurements.proto
    protoc --python_out=.. nbiot_device_info.proto
    protoc --python_out=.. proto_cloud_token_config.proto
    protoc --python_out=.. proto_config.proto
    protoc --python_out=.. proto_device_info.proto
     protoc --python_out=.. proto_nvstore.proto
    protoc --python_out=.. proto_rule.proto
    
