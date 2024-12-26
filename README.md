# Expo Camera `onBarCodeScanned` Inconsistency

This repository demonstrates a bug in Expo's Camera API where the `onBarCodeScanned` callback function does not reliably fire when barcodes are detected. The camera itself seems to be working correctly; however, the event listener fails to trigger consistently, resulting in missed scans.

## Bug Reproduction

1. Clone this repository.
2. Run `npm install` or `yarn install` to install dependencies.
3. Run the app using `expo start`.
4. Point the camera at a barcode.  You will notice that sometimes the `onBarCodeScanned` function is called, while other times it is not, even when the same barcode is scanned under seemingly identical conditions.

## Potential Causes

* **Underlying platform inconsistencies:** The issue may stem from discrepancies in how barcode scanning is handled across different platforms (iOS vs. Android).
* **Camera settings or configurations:** Specific camera configurations or settings might interfere with the event triggering.
* **Race conditions or timing issues:**  A race condition could exist between the barcode detection and the callback execution.
* **Expo library bug:**  There might be a bug within the Expo Camera library itself.

## Workaround (See bugSolution.js)

While the root cause remains unclear, using the `BarcodeScanner` component and periodically polling for results (as implemented in `bugSolution.js`) provides a workaround for this unreliable event callback behavior.