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
