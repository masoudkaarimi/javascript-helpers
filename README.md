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

## Convert Enter (\n) characters to lists

```js
const convertEnterToList = (text) => {
    if (text.match(/\n/) && !text.includes('<ul')) {
        let listText = text.split('\n');
        let list = '';

        for (let i = 0; i < listText.length; i++) {
            if (listText[i] != '') {
                list += `<li>${listText[i]}</li>`;
            }
        }
        return `<ul>${list}</ul>`;
    } else {
        return `<span>${text}</span>`;
    }
};

convertEnterToList('High quality\nThe best\nAwesome\nWonderful') // Result
// <ul>
// <li>High quality</li>
// <li>The best</li>
// <li>Awesome</li>
// <li>Wonderful</li>
// </ul>
```

```js
const timerCounter = (duration) => {
    let timer = parseInt(duration);
    let minutes, seconds;

    setInterval(function () {
        minutes = parseInt(timer / 60, 10);
        seconds = parseInt(timer % 60, 10);

        minutes = minutes < 10 ? '0' + minutes : minutes;
        seconds = seconds < 10 ? '0' + seconds : seconds;

        console.log(minutes + ':' + seconds);

        if (--timer < 0) {
            timer = 0;
        }
    }, 1000);
};
```

## Find the day of the year

```js
const getDayOfYear = (date) => {
    return Math.floor((date - new Date(date.getFullYear(), 0, 0)) / 1000 / 60 / 60 / 24)
}

getDayOfYear(new Date('2022-02-02')) // 33
getDayOfYear(new Date('2001-10-26')) // 299
getDayOfYear(new Date('2022-12-31')) // 365

```

## Date validity test

```js
const isDateValid = (...value) => !Number.isNaN(new Date(...value).valueOf())

isDateValid("Wed Feb 02 2022 09:49:38") // true
isDateValid("Wed Fd 02 2022 09:49:38") // false
```


## Find the number of days between two dates

```js
const getDayDifference = (date1, date2) => {
    return Math.ceil(Math.abs(date1.getTime() - date2.getTime()) / 86400000)
}

getDayDifference(new Date("2001-10-26"), new Date("2022-10-26")) // 7670
getDayDifference(new Date("2022-1-1"), new Date("2022-2-1")) // 31
```

## Random HEX code generation

```js
const randomHEXCode = () => `#${Math.floor(Math.random() * 0xfffffff).toString(16).padEnd(6, '0')}`

randomHEXCode() // #...
```

# The average of numbers calculation
```js
const average = (...args) => (args.reduce((a, b) => a + b) / args.length).toFixed(2)

average(15, 20, 18, 10, 12) // '15.00'
```


# Add in the future

- localStorage
- API instance
- CSRF Token
- File Size Units
- Cookie
