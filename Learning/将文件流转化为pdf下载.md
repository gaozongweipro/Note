# 将文件流转化为pdf下载
1. 从后端获取文档流
2. 前端将获取到的base64文档流转化为pdf文档流
3. 将pdf文档流通过a标签进行下载  
   
```
/**
 * 将文件流转化为pdf
 * @param data base64文件流
 * @returns {Blob}
 */
export function dataURLBlob(data) {
  let bstr = atob(data); // 解码base64的字符串， 返回解码后的字符串 bota编码方法
  let n = bstr.length;
  let u8arr = new Uint8Array(n); // 创建初始化为0， 包含n个元素的无符号整型数组
  while (n--) {
    u8arr[n] = bstr.charCodeAt(n); // 返回bstr字符的n位置的Unicode编码
  }
  return new Blob([u8arr], { type: 'application/pdf' });
}
```

```
/**
 * 下载文件
 * @param blob pdf文件流
 * @param fileName 下载的文件名
 */
export function downloadFile(blob, fileName) {
  if (window.navigator.msSaveOrOpenBlob) { // msSaveOrOpenBlob方法返回bool值
    navigator.msSaveBlob(blob, fileName); //本地保存
  } else {
    let link = document.createElement('a'); //a标签下载
    link.href = window.URL.createObjectURL(blob);
    link.download = fileName;
    link.click();
    window.URL.revokeObjectURL(link.href);
  }
}
```