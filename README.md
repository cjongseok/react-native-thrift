# react-native-thrift

Patched version of Apache Thrift Node.js library to work with React Native.

### Usage
It is necessary to replace all `require('thrift')` with `require('react-native-thrift')` in the thrift generated files. You may use `sed` for that:
```sh
for f in <gen_folder>/*; do
  sed -i '' -e \"s/'thrift'/'react-native-thrift'/\" $f
done`
```
