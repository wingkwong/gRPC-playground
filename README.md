# gRPC-playground
My gRPC Playground

## Define a protocol message

- Name of the message: UpperCamelCase
- Name of the field: lower_snake_case
- Some scalar-value data types:
    - string, bool, bytes
    - float, double
    - int32, int64, unit32, unit64, sint32, sint64, etc.
- Data types can be user-defined enums or other messages
    - is an arbitrary interger
        - from 1 to 2^29-1
        - except from 19,000 to 19,999 (reserved)
    - from 1 to 15 take 1 byte
    - don't need to be in-order or sequential
    - must be unique for same-level fields

```
syntax = "proto3"

message <NameOfTheMessage> {
    <data-type> name_of_field_1 = tag_1;
    <data-type> name_of_field_2 = tag_2;
    <data-type> name_of_field_3 = tag_3;
}
```

## Install

Install protobuf
```bash
brew install protobuf
```

Install gRPC
```bash
export GO111MODULE=on # Enable module-aware mode
go get google.golang.org/grpc@v1.28.1
```

Install ``protoc`` plugin for Go
```bash
go get github.com/golang/protobuf/protoc-gen-go
```

Update ``PATH`` so that the ``protoc`` compiler can find the plugin:
```
export PATH="$PATH:$(go env GOPATH)/bin"
```

## Generate gPRC Code
```
protoc proto/*.proto --go_out=plugins=grpc:pkg
```