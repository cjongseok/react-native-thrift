# react-native-thrift

Patched version of Apache Thrift Node.js library to work with React Native.

### Usage
It is necessary to replace all `require('thrift')` with `require('react-native-thrift')` in the thrift generated files. You may use `sed` for that:
```sh
for f in <gen_folder>/*; do
  sed -i '' -e \"s/'thrift'/'react-native-thrift'/\" $f
done`
```

---

To be able using `TCompactProtocol` or `TBinaryProtocol` you should install and import `react-native-fetch-blob` package. _Unfortunately I haven't found correct way to send binary data to be recognized by thrift server using default react-native XMLHttpRequest shim._
```
npm install react-native-fetch-blob --save
react-native link react-native-fetch-blob
```

And then replace `XMLHttpRequest` with the `react-native-fetch-blob` polyfill.
```
import rnfetch from 'react-native-fetch-blob';
window.XMLHttpRequest = rnfetch.polyfill.XMLHttpRequest;
```
