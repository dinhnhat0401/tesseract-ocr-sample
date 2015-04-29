# tesseract-ocr-sample

## tesseract about

Tesseract OCR is quite powerful, but does have the following limitations:

* Unlike some OCR engines (like those used by the U.S. Postal Service to sort mail)

* Tesseract is unable to recognize handwriting and is limited to about 64 fonts in total.
* Tesseract requires a bit of preprocessing to improve the OCR results; images need to be scaled appropriately, have as much image contrast as possible, and have horizontally-aligned text.
* Finally, Tesseract OCR only works on Linux, Windows, and Mac OS X.

## Perform image recognize code

```
    func performImageRecognition(image: UIImage) {
    // 1
    let tesseract = G8Tesseract()

    // 2
    tesseract.charWhitelist="0123456789円¥";
      
    tesseract.language = "eng+jpn"

    // 3
    tesseract.engineMode = .TesseractOnly

    // 4
    tesseract.pageSegmentationMode = .Auto
    
    // 5
    tesseract.maximumRecognitionTime = 60.0

    // 6
    tesseract.image = image.g8_blackAndWhite()
    tesseract.recognize()

    // 7
    textView.text = tesseract.recognizedText
    textView.editable = true
    
    // 8
    removeActivityIndicator()
  }
}
```

## Tesseract test result

| No   |      image url      |  recognizable ?(x/o) | Result |
|------|:-------------------:|---------------------:|-------:|
| 1 | ![](http://i.gyazo.com/8b2f17aef83aa8bedafa32391e852606.png) |    x |       |
| 2 | ![](http://i.gyazo.com/e631a5c603293097240a0d37a91ab63a.png) |    o |  ¥1873|
| 3 | ![](http://i.gyazo.com/28d7db954d174fb013d28598343e4411.png) |    o |  999円|
| 4 | ![](http://i.gyazo.com/5c1a3c1c080bc455325c8d11d3591d73.png) |    x |       |
| 5 | ![](http://i.gyazo.com/97f70ea04b70a72b2bb15c064df5f494.png) |    o |  999円|
| 6 | ![](http://i.gyazo.com/baae790e0f0ba339ac3685783065c7fe.png) |    x |       |
| 7 | ![](http://i.gyazo.com/ad68fab8e62aad70b5cb330f1be0821e.png) |    o |¥2023  |

## References

* http://www.raywenderlich.com/93276/implementing-tesseract-ocr-ios

* https://code.google.com/p/tesseract-ocr/wiki/FAQ
