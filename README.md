# Installing Spl33t3r max4live on Windows For Dummies

Non Docker install instructions.

### Download the Zip
https://github.com/diracdeltas/spleeter4max/releases/download/1.4-native/spleeter-native.zip

Extract it somewhere you can remember.

### Install Choco 

Installing the choco package manager removes any chance of you having to do anything manual / install other pre-requirements for that software. The packages come with installations tasks that install other things that might be needed. Hence why were using it here as its more or less fool proof.

Open Powershell --> Run As Administrator

Run the following to install choco:
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Verify its installed:
```
PS C:\Windows\system32> choco
Chocolatey v0.10.15
Please run 'choco -?' or 'choco <command> -?' for help menu.
```

### Install dependancies:
```
choco install -y ffmpeg
choco install -y python --version=3.7.2
```

Verify they work - python needs to be 3.7 for this application to run. If you know how to run multiple different python versions, then you dont need me telling you how :)
You will need to do this in a new shell (close the powershell window or typing ```Invoke-Command { & "powershell.exe" } -NoNewScope``` in the same Window)
```
PS C:\Windows\system32> python --version
Python 3.7.2
```

```PS C:\Windows\system32> ffmpeg
ffmpeg version 4.3 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 9.3.1 (GCC) 20200621
  configuration: --enable-gpl --enable-version3 --enable-sdl2 --enable-fontconfig --enable-gnutls --enable-iconv --enable-libass --enable-libdav1d --enable-libbluray --enable-libfreetype --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libopenjpeg --enable-libopus --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libsrt --enable-libtheora --enable-libtwolame --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxml2 --enable-libzimg --enable-lzma --enable-zlib --enable-gmp --enable-libvidstab --enable-libvmaf --enable-libvorbis --enable-libvo-amrwbenc --enable-libmysofa --enable-libspeex --enable-libxvid --enable-libaom --enable-libgsm --disable-w32threads --enable-libmfx --enable-ffnvcodec --enable-cuda-llvm --enable-cuvid --enable-d3d11va --enable-nvenc --enable-nvdec --enable-dxva2 --enable-avisynth --enable-libopenmpt --enable-amf
  libavutil      56. 51.100 / 56. 51.100
  libavcodec     58. 91.100 / 58. 91.100
  libavformat    58. 45.100 / 58. 45.100
  libavdevice    58. 10.100 / 58. 10.100
  libavfilter     7. 85.100 /  7. 85.100
  libswscale      5.  7.100 /  5.  7.100
  libswresample   3.  7.100 /  3.  7.100
  libpostproc    55.  7.100 / 55.  7.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
```

### Removing Environment Variables
You can do this through pwoershell, but you risk nuking your env variables if you mess that up. N00b friendly way is like this:

1. Start --> Search for System Environment --> Edit the System Environment Variables.
2. Remove the .JS extension from PATHEXT.

Pictures Below show how to do this:

### Installing Spleeter itself:
As the guide says, use pip to install this. This installs python packages and will install the spleeter python package.

```
pip install spleeter
```

Should be obvious when that is installed:
7.jpg


Try and run spleeter:
```
C:\Windows\system32>spleeter -h
usage: spleeter [-h] {separate,train,evaluate} ...

positional arguments:
  {separate,train,evaluate}
    separate            Separate audio files
    train               Train a source separation model
    evaluate            Evaluate a model on the musDB test dataset

optional arguments:
  -h, --help            show this help message and exit
```

If it doesnt work, try running in a new powershell / cmd window.

### Test things are working:

```
curl -o check-install.py https://raw.githubusercontent.com/diracdeltas/spleeter4max/feature/native-spleeter/check-install.py
python check-install.py
```

You should see no errors:
```
PS C:\Users\Jeremy\Downloads> python check-install.py
Checking install...
Done. If no errors printed, you might be good to go! Make sure Ableton is 10.1+ and Max is 8.1+.
```

**This should mean you are good to go.** ...well might be.

### Verify it works in Ableton.

1. Open ableton. 
2. Go back to the extracted folder of spleeter native.
3. Double click on spleeter-native.amxd. 
4. Load a clip into an Audio Channel with spleeter. 
5. Click Start

This will create a folder in the folder where spleeter is running from  (where you extracted).
You should then see the files.

This should work. If it doesnt hit me up. 
