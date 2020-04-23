# Imagick  Pdf 2 Image



## imagick

### GitHub地址

https://github.com/gographics/imagick

### 文档地址

https://godoc.org/gopkg.in/gographics/imagick.v2/imagick



## Install-Mac

```shell
# 安装依赖imagemagick，底层调用c库imagemagick实现
brew install imagemagick
```



##  验证pkg-config 正确使用ImageMagic

```shell
pkg-config --cflags --libs MagickWand
```

终端输出

```shell
-Xpreprocessor -fopenmp -DMAGICKCORE_HDRI_ENABLE=1 -DMAGICKCORE_QUANTUM_DEPTH=16 -Xpreprocessor -fopenmp -DMAGICKCORE_HDRI_ENABLE=1 -DMAGICKCORE_QUANTUM_DEPTH=16 -I/usr/local/Cellar/imagemagick/7.0.10-7/include/ImageMagick-7 -L/usr/local/Cellar/imagemagick/7.0.10-7/lib -lMagickWand-7.Q16HDRI -lMagickCore-7.Q16HDRI
```

## 获取Imagick

```shell
go get gopkg.in/gographics/imagick.v3/imagick
```



## 遇到问题

### cgo安全限止 -Xpreprocessor

```shell
# 配置环境变量
export CGO_CFLAGS_ALLOW='-Xpreprocessor'
```



### 版本不匹配

```shell
../go/pkg/mod/gopkg.in/gographics/imagick.v2@v2.6.0/imagick/affine_matrix.go:8:10: fatal error: 'wand/MagickWand.h' file not found
```

```shell
# 版本兼容，可见imagick github
We support two compatibility branches:

master (tag v2.x.x): 6.9.1-7 <= ImageMagick <= 6.9.9-35
im-7   (tag v3.x.x): 7.x     <= ImageMagick <= 7.x
legacy (tag v1.x.x): 6.7.x   <= ImageMagick <= 6.8.9-10
They map, respectively, through gopkg.in:

gopkg.in/gographics/imagick.v2/imagick
gopkg.in/gographics/imagick.v3/imagick
gopkg.in/gographics/imagick.v1/imagick
```



## 示例代码

创建PDF

```go
package main

import (
	"fmt"
	"log"

	"github.com/signintech/gopdf"
)

const family = "HDZB_5"

func main() {
	pdf := gopdf.GoPdf{}
	pdf.Start(gopdf.Config{PageSize: gopdf.Rect{ // A4
		W: 595.28,
		H: 841.89,
	}})

	pdf.AddPage()
	err := pdf.AddTTFFont("HDZB_5", "/Users/user/Library/Fonts/SimSun.ttf")
	if err != nil {
		log.Print(err.Error())
		return
	}

	err = pdf.SetFont(family, "", 34)
	if err != nil {
		log.Println(err.Error())
	}
	pdf.SetGrayFill(0.5)
	pdf.Cell(nil, "您好")
	pdf.WritePdf("/Users/user/Desktop/hello.pdf")
	fmt.Println("done")

}

```

PDF 2 image

```go
package main

import (
	"fmt"
	"gopkg.in/gographics/imagick.v3/imagick"
	"strconv"
	"time"
)

/*
mac os i5 8G
两页PDF转图片
go spent time：739ms
java spent time：6528ms
*/
func main() {
	sTime := time.Now().UnixNano() / 1e6
	fmt.Println(time.Now())
	imagick.Initialize()
	defer imagick.Terminate()
	mw := imagick.NewMagickWand()
	defer mw.Destroy()

	mw.ReadImage("/Users/user/Desktop/testData/test.pdf")
	number := mw.GetNumberImages()
	fmt.Println("page=", number)
	for i := 0; i < int(number); i++ {
		mw.SetImageCompression(imagick.COMPRESSION_JPEG)
		fmt.Println(int(number))
		fmt.Println("i:", i)
		mw.SetIteratorIndex(i)
		mw.SetImageFormat("png")
		fmt.Println("str i", string(number))
		path := "/Users/user/Desktop/hello" + strconv.Itoa(i) + ".png"
		fmt.Println("path=", path)
		mw.WriteImage(path)
	}

	fmt.Println("spent time:", (time.Now().UnixNano()/1e6)-sTime)

}

```



## 图片相关处理

### imagick去除边框

https://www.jianshu.com/p/38998264182d

### 绘制复杂图片

https://www.jianshu.com/p/38998264182d

## 参考

### imageick安装

https://raw.githubusercontent.com/qloog/lnmp100.github.io/master/content/note/install-imagemagick-and-the-imageick-extensions-of-php-on-mac.md

### PDF转jpg

https://studygolang.com/topics/10726

### imagick pdf 2 image

https://blog.csdn.net/yuyinghua0302/article/details/79637905