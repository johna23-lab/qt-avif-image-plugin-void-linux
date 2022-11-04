# qt-avif-image-plugin
Qt plug-in to allow Qt and KDE based applications to read/write AVIF images.

Manual **How to install AVIF support in KDE**

## What is AVIF?

**AV**1 **I**mage File **F**ormat (AVIF) is an advanced image format [specified](https://aomediacodec.github.io/av1-avif/) by [Alliance for Open Media](https://aomedia.org/).

AVIF is technically a picture compressed with AV1 video codec wrapped in ISO Base Media File Format.  
AV1 compression provides significantly better efficiency than traditional JPEG. Beside 8bit per channel AVIF allows 10bit and 12bit depth, transparency, color profiles, metadata, animation, compression quality ranging from visually lossless to highly compressed lossy while maintaining decent visual quality at low bitrates.

## Download and install the compiled version for linux void

`wget https://github.com/johna23-lab/qt-avif-image-plugin-void-linux/releases/download/1.0_1/avif-lib-qt5-1.0_1.x86_64.xbps `

`xbps-rindex -a avif-lib-qt5-1.0_1.x86_64.xbps`

`sudo xbps-install -R $PWD avif-lib-qt5-1.0_1`

## 1) Download to compile

`git clone https://github.com/nomacs/qt-avif-image-plugin.git`

`cd qt-avif-image-plugin`

## 2) Adding MIME types

In order to install mime types **image/avif** and **image/avif-sequence** in your system, copy (as root) _avif.xml_, _avifs.xml_ files to _/usr/share/mime/packages/_ folder and run:

`update-mime-database /usr/share/mime`

![avif.xml](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/avif_xml.png)  
![avifs.xml](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/avifs_xml.png)

## 3) Compile Qt Image Plugin

Qt Image Plugin allows Qt and KDE applications to open/save pictures in AVIF format. The plug-in uses [libavif](https://github.com/AOMediaCodec/libavif/) internally.  
You need Qt5 development packages (for example qtbase5-dev), qmake, you may also need cmake and yasm.

If your system has libavif installed (at least version 0.6.0, check for the presence of _/usr/include/avif/avif.h_), run:

`./build_libqavif_dynamic.sh` 
![](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/build_libqavif_dynamic.png)

If you don't have libavif installed, run:

`./build_libqavif_static.sh` 
![](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/build_libqavif_static.png)

## 4) Install libqavif.so

Copy **libqavif.so** to a folder where _qt5-image-formats-plugins_ and/or _kimageformats_ are installed. It could be one of these locations:

*   /usr/lib/qt5/plugins/imageformats
*   /usr/lib/qt/plugins/imageformats/
*   /usr/lib/x86_64-linux-gnu/qt5/plugins/imageformats

![installed libqavif.so in /plugins/imageformats](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/imageformats.png)

## 5) Associate *.avif with applications

Qt based applications should be able to open [AVIF](https://github.com/AOMediaCodec/av1-avif/tree/master/testFiles) images now.  
Example how to associate AVIF file type with _gwenview_:  
![](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/association.png)

## 6) Enable AVIimg/app_qview.pnF thumbnails in dolphin file manager

Copy _avif.desktop_, _avifs.desktop_ to:  
*/usr/share/kservices5/qimageioplugins/*

Update _imagethumbnail.desktop_ (in /usr/share/kservices5/ ):  
Add `;image/avif;image/avif-sequence` to the `MimeType=` list:  
![](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/imagethumbnail.png)

AVIF thumbnails in dolphin:  
![](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_dolphin.png)

## 7) Enjoy using AVIF in applications

### gwenview

![AVIF picture in gwenview](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_gwenview.png)

### KolourPaint

![AVIF picture in kolourpaint](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_kolourpaint.png)

### nomacs

![AVIF images in nomacs](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_nomacs.png)

### KPhotoAlbum

![AVIF images in kphotoalbum](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_kphotoalbum.png)

### digiKam

![AVIF images in digikam](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_digikam.png)

### qView

![AVIF image in qView](https://github.com/nomacs/qt-avif-image-plugin/raw/master/img/app_qview.png)
