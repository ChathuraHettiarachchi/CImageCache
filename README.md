# CImageCache
This library can download images from URL and save them inside your external storage. If device does not have external storage it takes device cache directory to store images downloaded from the URL provided. Library used Asyn to download images and they want show in gallery. Mostly useful if apps need to cache images from url tile images changed.

![logo_image](https://cloud.githubusercontent.com/assets/13764097/15285396/768100ae-1b74-11e6-9c8a-f664593eee5d.png)

####Ok now let's take a look how to intergrate this lib with your application.

For the android project just include the following dependency inside you buil.gradle's depedency list.

Gradle
------
```
dependencies {
    ...
    compile 'com.chootdev:cimagecache:1.0.3'
}
```

if you using maven use following
Maven
------
```
<dependency>
  <groupId>com.chootdev</groupId>
  <artifactId>cimagecache</artifactId>
  <version>1.0.3</version>
  <type>pom</type>
</dependency>
```

After that the only thing you need to do to save and use the image is to call the following method. This method taking image URL and ImageView as the parameters. CImageCache save images using there URL name by substring theme. so it can easily identify if the URL gets changed.

As the lib's first call, this will create folder from application name. So nothing to worry.

Usage
-----
```java
CImageLoader loader = new CImageLoader(this);
loader.DisplayImage(YOUR_IMAGE_URL,YOUR_IMAGE_VIEW);
```

if you need to set custom placeholder just send your resource id with the call of constructor as follows,
```java
CImageLoader loader = new CImageLoader(this, R.id.PLACE_HOLDER);
loader.DisplayImage(YOUR_IMAGE_URL,YOUR_IMAGE_VIEW);
```

this library make images compress for the good of memory management. So as the default, images are resize to around 400px. It'll not affect to any resolution issues.

if you need to set scaleType to the image, use
```java
CImageLoader loader = new CImageLoader(this);
loader.DisplayImage(YOUR_IMAGE_URL,YOUR_IMAGE_VIEW,SCALE_TYPE); 

/*
*CImageConst.CENTER
*CImageConst.CENTER_CROP
*CImageConst.CENTER_INSIDE
*CImageConst.FIT_CENTER
*CImageConst.FIT_XY
*CImageConst.FIT_END
*CImageConst.FIT_START
*CImageConst.FIT_MATRIX
*/
```
This lib also support taking full size image from your device cache.
```java
CImageLoader loader = new CImageLoader(this, R.id.PLACE_HOLDER);
Bitmap image = loader.getFullImage(YOUR_URL); // this will return bitmap.
```
to get resize image and default size image (400px) just call below methods.
```java
CImageLoader loader = new CImageLoader(this, R.id.PLACE_HOLDER);
Bitmap image = loader.getBitmap(YOUR_URL); // resized image (400px)

Bitmap image = loader.getBitmap(YOUR_URL, YOUR_SIZE); // custom size
```
if you decide to clear app cache memory that holds images, (Like some apps use reset data to make app fresh)
you can use this method to do so.
```java
CImageLoader loader = new CImageLoader(this, R.id.PLACE_HOLDER);
loader.clearCache();
```

Changelog
---------
* **1.0.3**
    * Stable release
* **1.0.2**
    * Set scaletype added
* **1.0.1**
    * Added support custom image sizes
* **1.0.0**
    * Initial release

# License
Copyright 2016 Chathura Hettiarachchi

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
