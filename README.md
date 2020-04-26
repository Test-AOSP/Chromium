Chromium (Hardened variant)
============================

Build instructions
------------------

Clone this repository:

```
git clone https://github.com/Test-AOSP/Chromium.git
cd Chromium
```

Get source code of the latest stable version of Chromium for Android

```
fetch --nohooks android
gclient sync -D --with_branch_heads -r 81.0.4044.117 --jobs 32
```

Apply the patches:

```
cd src
git am --whitespace=nowarn ../patches/*.patch
```

Compile the apks:

```
gn args out/Default # Copy the configuration from ../args.gn
ninja -C out/Default/ trichrome_webview_apk trichrome_chrome_bundle trichrome_library_apk
```
