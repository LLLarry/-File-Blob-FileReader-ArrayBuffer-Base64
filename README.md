# 彻底搞懂：File、Blob、FileReader、ArrayBuffer、Base64

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/cf702f942b5840ada87a079d2ad090c3.png)

**Blob**

> Blob 全称为 binary large object ，即二进制大对象。blob对象本质上是js中的一个对象，里面可以储存大量的二进制编码格式的数据。Blob 对象一个不可修改，从Blob中读取内容的唯一方法是使用 FileReader。

① 创建

> new Blob(array,options)
> 其有两个参数：
> array：由 ArrayBuffer、ArrayBufferView、Blob、DOMString 等对象构成的，将会被放进 Blob；
> options：它可能会指定如下两个属性
> type：默认值为 ""，表示将会被放入到 blob 中的数组内容的 MIME 类型。
> endings：默认值为"transparent"，用于指定包含行结束符\n的字符串如何被写入，不常用。

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/5c6c19d8e16345979a2b609d12deec6d.png)

演示：

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/b29d70be5543435a8543085a165212a4.png)

> 这个 blob 对象上有两个属性：

size：Blob对象中所包含数据的大小（字节）；
type：字符串，认为该Blob对象所包含的 MIME 类型。如果类型未知，则为空字符串。

②分片

> Blob 对象内置了 slice() 方法用来将 blob 对象分片

其有三个参数：
start：设置切片的起点，即切片开始位置。默认值为 0，这意味着切片应该从第一个字节开始；
end：设置切片的结束点，会对该位置之前的数据进行切片。默认值为blob.size；
contentType：设置新 blob 的 MIME 类型。如果省略 type，则默认为 blob 的原始值。

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/1aeb0bbb4643482ab407c30f3572c848.png)

**File**

> File 对象是特殊类型的 Blob，

在 JavaScript 中，主要有两种方法来获取 File 对象：
（1） 元素上选择文件后返回的 FileList 对象；
（2）文件拖放操作生成的 DataTransfer 对象；

演示一下：

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/20d444edad184cdb9838bec211b7ffd4.png)

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/4ccd4a7dacec4f028a8fff2025f28843.png)

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/797c5e9746e24973ae0426b6440b56a0.png)

**Filereader**

> 通过上面我都知道了blob是不可修改也是无法读取里面的内容的。无法读取里面的内容肯定是不可行的。
> 所以Filereader就提供了读取blob里面内容的方法

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/5e5300b2bfc94511897ee69b248e56b4.png)

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/52079027d9b0438c83e54d7946ce62a0.png)

这里演示一下：

①将文件读取为base64

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/548c3e4971354cf08179df9c2baf6d85.png)

②将存入的字符串的blob对象，读出来里面的内容

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/6452efa9910941b2965fa1c9f777437a.png)

**ArrayBuffer**

> 我们可以把它理解为特殊的数组，特殊在哪里呢？
> ArrayBuffer 本身就是一个黑盒，不能直接读写所存储的数据，需要借助以下视图对象来读写
> TypedArray只是一个概念，实际使用的是那9个对象

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/0063558fe53c4a0ea11f53312c4efd54.png) ![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/3f779660ddbb4f4ebc415a5dc9df4f9c.png)

①创建buffer

> new ArrayBuffer(bytelength)
> 参数：它接受一个参数，即 bytelength，表示要创建数组缓冲区的大小（以字节为单位。）

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/42378036f01b4bb9913379cfb9e4af9a.png)

②TypedArray读写buffer

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/431466d006a04eef8b79f4374c8edeea.png)

③DataView读写buffer

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/767941a4991d413abd1f891021443ad8.png)

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/a851210344e84c3aa142b352c3df934a.png)

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/6392e7b7eaa04cc1a13370ec690f7337.png)

**Object URL**

> 它是一个用来表示File Object 或Blob Object 的URL

演示一下：

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/7fe2356e25704f3b86fc4e745893dc3e.png)

**base64**

>在 JavaScript 中，有两个函数被分别用来处理解码和编码 _base64_ 字符串：

* atob()：解码，解码一个 Base64 字符串；
* btoa()：编码，从一个字符串或者二进制数据编码一个 Base64 字符串。

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/a1f0625bfdb64d07980618cbc86fa872.png)

> 主要使用：
> ①将canvas画布内容生成base64的图片
> ②将获取的图片文件，生成base64图片【这个在上面的filereader的时候已经演示过了，这里就不演示了】
> 演示①：

![ ](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/9037785a6ec24d80b6ca08c7806b1d98.png)

**总结：**

1.ArrayBuffer 与 Blob 有啥区别呢？根据 ArrayBuffer 和 Blob 的特性，Blob 作为一个整体文件，适合用于传输；当需要对二进制数据进行操作时（比如要修改某一段数据时），就可以使用 ArrayBuffer。

2.通过ArrayBuffer创建Blob,然后通过FileReader读取里面的内容

![](https://blog-1302889287.cos.ap-nanjing.myqcloud.com/%E5%BD%BB%E5%BA%95%E6%90%9E%E6%87%82%EF%BC%9AFile%E3%80%81Blob%E3%80%81FileReader%E3%80%81ArrayBuffer%E3%80%81Base64/95af452a7db4439eb49847a8be28136e.png)



### 示例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ArrayBuffer</title>
    <style>
        .drag-box {
            width: 300px;
            height: 300px;
            border-radius: 10px;
            border: 1px dotted deepskyblue;
        }
    </style>
</head>
<body>
    <h3>ArrayBuffer</h3>
    <div class="drag-box"></div>
    <video src="" id="video"></video>
    <script>
        const dragBox = document.querySelector('.drag-box')
        const video = document.querySelector('#video')
        dragBox.ondragover = (e) => {
            e.preventDefault()
        }
        dragBox.ondrop = (e) => {
            e.preventDefault()
            // 拖拽的file对象
            const file = e.dataTransfer.files[0]
            // 复制文件
            copyFile(file)
            // 1、转化为临时连接
            // console.log(file, URL.createObjectURL(file))
            // 2、通过fileReader转化为base64位
            const reader = new FileReader()
            reader.onload = (e) => {
                // 文件大小141720和字节
                console.log(e.target.result) // ArrayBuffer(141720)
                
                const arraybuffer = e.target.result
                
                // 有符号 每位占1个字节
                const int8buffer = new Int8Array(arraybuffer) // Int8Array(141720) [-119, 80, 78, 71, 13, 10, 26, 10, 0, 0, 0, 13, 73, 72, 68, 82, 0, 0, 3, 32, 0, 0, 1, -32, 8, 6, 0, 0, 0, 93, 7, 9, -11, 0, 0, 0, 1, 115, 82, 71, 66, 0, -82, -50, 28, -23, 0, 0, 32, 0, 73, 68, 65, 84, 120, 94, -20, -99, 7, 120, 20, -27, 22, -122, -33, 36, -101, 100, 55, -69, -23, -95, -93, -128, -120, 34, 40, -94, 98, -63, 2, -40, 65, -67, -94, 98, 1, 68, 17, 69, -79, 96, 69, -63, 2, 98, -63, -118, 98, 69, …]
                // 无符号 每位占1个字节
                const uint8buffer = new Uint8Array(arraybuffer) // Uint8Array(141720) [137, 80, 78, 71, 13, 10, 26, 10, 0, 0, 0, 13, 73, 72, 68, 82, 0, 0, 3, 32, 0, 0, 1, 224, 8, 6, 0, 0, 0, 93, 7, 9, 245, 0, 0, 0, 1, 115, 82, 71, 66, 0, 174, 206, 28, 233, 0, 0, 32, 0, 73, 68, 65, 84, 120, 94, 236, 157, 7, 120, 20, 229, 22, 134, 223, 36, 155, 100, 55, 187, 233, 161, 163, 128, 136, 34, 40, 162, 98, 193, 2, 216, 65, 189, 162, 98, 1, 68, 17, 69, 177, 96, 69, 193, 2, 98, 193, 138, 98, 69, …]
                // 有符号 每位占2个字节
                const int16buffer = new Int16Array(arraybuffer) // Int16Array(70860) [20617, 18254, 2573, 2586, 0, 3328, 18505, 21060, 0, 8195, 0, -8191, 1544, 0, 23808, 2311, 245, 0, 29441, 18258, 66, -12626, -5860, 0, 32, 17481, 21569, 24184, -25108, 30727, -6892, -31210, 9439, 25755, -17609, -24087, -32605, 8840, -24024, -16030, -10238, -17087, 25250, 17409, 17681, 24753, -16059, 25090, -30015, 17762, 14257, 16448, -29756, -23926, -32216, -32246, 1416, 1105, 10921, -28611, -27682, 32205, -13122, -19738, -4924, 30566, 27795, -15498, -6244, 29409, -26155, -7, -13057, -13076, -12673, -12551, 17911, -6912, 25080, 10047, -14526, 10248, -32209, 8856, -30008, -895, 26648, 12533, -31888, -24207, 5250, -27416, 6913, -18179, 31150, -6040, -8069, 22709, -3400, -14332, …]
                console.log(int8buffer, uint8buffer, int16buffer)
            }
            reader.readAsArrayBuffer(file)
        }

        // 复制文件
        // 思路： 将file文件通过FileFeader读取为ArrayBuffer形式，由于ArrayBuffer不允许我们直接操作所以我们要使用他的TypedView来进行操作
        // 我们封装一个通用的复制、所以我们采取按照每个字节去复制，所以 使用Int8Array类来操作二进制数据（每一项占用1个字节）
        // 我们新建一个Int8Array实例，长度和旧的Int8Array一致
        // 然后将就Int8Array中的每一项数据都拷贝到新的Int8Array中
        // Int8Array.buffer获取新的ArrayBuffer
        // new Blob([新的ArrayBuffer], { type: 'xxx' }) 获取新的blob
        // 然后blob可以生成对应的临时连接或者base64
        function copyFile (file) {
            const reader = new FileReader()
            reader.onload = (e) => {
                console.log('e.target.result', )
                const arrayBuffer = e.target.result
                // arrayBuffer不能直接操作、要转化为可以操作的类数组
            const int8Array = new Int8Array(arrayBuffer)
            // 创建一个字节数和arrayBuffer一致的类数组 （这里使用Int8Array,就是每每次写入一个新字节）
            const newInt8Array = new Int8Array(arrayBuffer.byteLength)
            // 写去到新
            for (let i = 0; i < int8Array.length; i++) {
                // if (i < arrayBuffer.byteLength / 2) {
                //     newInt8Array[i] = int8Array[i]
                // }
                newInt8Array[i] = int8Array[i]
            }
            // 将Int8Array转化为ArrayBuffer
            const newArrayBuffer = newInt8Array.buffer
            // 将ArrayBuffer转化为Blob对象
            const blob = new Blob([newArrayBuffer], { type: file.type })
            // 将blob对象转化为临时地址来使用
            const onceUrl = URL.createObjectURL(blob)
            console.log(onceUrl)
            }
            reader.readAsArrayBuffer(file)
            
            
        }
    </script>
</body>
</html>
```

