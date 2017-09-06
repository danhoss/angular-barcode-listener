# Angular Barcode Listener

Listen for barcode scanner events in your Angular application

## Usage

Install from:

- Bower: `bower install angular-barcode-listener`

```javascript
var app = angular.module('app', ['barcodeListener']);
```

```html
<barcode-listener
  on-scan='ctrl.handleScan'
  prefix='P%'
  length='24'
  scan-duration='500'
></barcode-listener>
```

## Configuration

- **prefix** - expected prefix for scan inputs
- **length** - expected length for scan inputs, not including prefix – *optional* - scans of different length will not be registered if this is provided
- **onScan** - callback to call after successful scan
- **scanDuration** - milliseconds duration for scan to complete (defaults to 50)

## Bookmarklet

If you need to simulate scanning a barcode while developing and don't have a scanner handy you can paste the following code into a bookmark which will prompt you to enter some text that you want "scanned":

```javascript
javascript:(function(){
  var $document = window.angular.element(document).injector().get('$document');

  var triggerKeypressEvent = function(char) {
    var event = new Event('keypress');
    event.which = char.charCodeAt(0);
    $document.triggerHandler(event);
  };

  var barcode = prompt('Text to scan');
  for (var i = 0; i < barcode.length; i++) {
    triggerKeypressEvent(barcode[i]);
  }
})();

```
$ git clone https://github.com/danhoss/angular-barcode-listener && cd angular-barcode-listener
$ npm install
$ npm test
