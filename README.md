# Javascript Helpers

Here are some commonly used functions you may use throughout the project

## Format File Size
 
```js
function formatFileSize(bytes, decimalPoint) {
    if (bytes == 0) return '0 Bytes';
    let k = 1000,
        dm = decimalPoint || 2,
        sizes = ['Bytes', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'],
        i = Math.floor(Math.log(bytes) / Math.log(k));
    return parseFloat((bytes / Math.pow(k, i)).toFixed(dm)) + ' ' + sizes[i];
}

console.log(formatFileSize(2)); // 2 Bytes
console.log(formatFileSize(2234)); // 2.23 KB);
console.log(formatFileSize(1220000)); // 1.22 MB);
console.log(formatFileSize(4250000000)); // 4.25 GB);
console.log(formatFileSize(1500000000000)); // 1.5 TB);
```

## Comma separator in the form of thousands

```js
const separatorWithComma = (Number) => {
    Number += '';
    Number = Number.replace(',', '');
    Number = Number.replace(',', '');
    Number = Number.replace(',', '');
    Number = Number.replace(',', '');
    Number = Number.replace(',', '');
    Number = Number.replace(',', '');
    let x = Number.split('.');
    let y = x[0];
    let z = x.length > 1 ? '.' + x[1] : '';
    let rgx = /(\d+)(\d{3})/;
    while (rgx.test(y)) y = y.replace(rgx, '$1' + ',' + '$2');
    return y + z;
};

separatorWithComma(0)          // '0'
separatorWithComma(100)        // '100'
separatorWithComma(1000)       // '1,000'
separatorWithComma(10000.5)    // '10,000.5'
separatorWithComma(100000.25)  // '100,000.25'
separatorWithComma(1000000)    // '1,000,000'
separatorWithComma(10000000)   // '10,000,000'
separatorWithComma(100000000)  // '100,000,000'

// or

const separatorWithComma = (x) => {
    return x.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
}

separatorWithComma(0)          // '0'
separatorWithComma(100)        // '100'
separatorWithComma(1000)       // '1,000'
separatorWithComma(10000.5)    // '10,000.5'
separatorWithComma(100000.25)  // '100,000.25'
separatorWithComma(1000000)    // '1,000,000'
separatorWithComma(10000000)   // '10,000,000'
separatorWithComma(100000000)  // '100,000,000'

// or 

const number = 10000000.25;
console.log(number.toLocaleString()); // 10,000,000.25
```

# Add in the future

- localStorage
- API instance
- CSRF Token
- File Size Units
- Cookie
