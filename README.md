# rn-honeywell-scanner

This module is fork of react-native-honeywell-scanner-v2 with a fallback fix for IOS and just experimenting with my first react native package upload

## Getting started

`$ npm install rn-honeywell-scanner --save`

## Usage
```javascript
import HoneywellScanner from 'rn-honeywell-scanner';

...

useEffect(() => {
        if( HoneywellScanner.isCompatible ) {
            HoneywellScanner.startReader().then((claimed) => {
                console.log(claimed ? 'Barcode reader is claimed' : 'Barcode reader is busy');
                HoneywellScanner.onBarcodeReadSuccess(event => {
                    console.log('Received data', event.data);
                });

            });


            return(
                () => {
                    HoneywellScanner.stopReader().then(() => {
                        console.log("Freedom!!");
                        HoneywellScanner.offBarcodeReadSuccess();
                    });
                }
            )
        }
    }, []);
```