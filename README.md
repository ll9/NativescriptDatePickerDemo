# get correct date from datepicker

first install this plugin: https://www.npmjs.com/package/nativescript-modal-datetimepicker

in order to get the correct date (independent of the timezone) use this:

var now = new Date();
var todayUTC = new Date(Date.UTC(now.getFullYear(), now.getMonth(), now.getDate()));
return todayUTC.toISOString().slice(0, 10).replace(/-/g, '');

(see: https://stackoverflow.com/questions/3066586/get-string-in-yyyymmdd-format-from-js-date-object)

# NativeScript-Vue Application

> A native application built with NativeScript-Vue

## Usage

``` bash
# Install dependencies
npm install

# Build for production
tns build <platform> --bundle

# Build, watch for changes and debug the application
tns debug <platform> --bundle

# Build, watch for changes and run the application
tns run <platform> --bundle
```