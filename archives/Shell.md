[⬆ 返回顶部 ⬆](#)

---

- [JPG -\> PDF](#jpg---pdf)
- [FLAC -\> M4A](#flac---m4a)
- [.bashrc](#bashrc)

---

## JPG -> PDF

```shell
convert \*.jpg my_pdf.pdf
```

## FLAC -> M4A

```shell
find . -iname '*.flac' -exec sh -c 'ffmpeg -i "$1" -map a:0 -c:a libfdk_aac -b:a 320k "${1%.flac}.m4a"' _ {} \;
find . -iname '*.flac' -exec sh -c 'ffmpeg -i "$1" -acodec libmp3lame -ab 320k "${f%.m4a}.mp3"' _ {} \;
```

## .bashrc

```shell
#alias
alias aptupdate='sudo apt update -y && sudo apt upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y'
alias androidstudio='nohup /usr/local/android-studio/bin/studio.sh > /dev/null 2>&1 &'
alias idea='nohup /usr/local/idea/bin/idea.sh > /dev/null 2>&1 &'
alias firefox='nohup firefox > /dev/null 2>&1 &'

#export
export NODE_MIRROR=https://mirrors.tuna.tsinghua.edu.cn/nodejs-release/
export FNM_NODE_DIST_MIRROR=https://mirrors.tuna.tsinghua.edu.cn/nodejs-release/
export DISPLAY=$(cat /etc/resolv.conf | grep nameserver | awk '{print $2; exit;}'):0.0
export LIBGL_ALWAYS_INDIRECT=1
export XMODIFIERS=@im=fcitx
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export ANDROID_HOME=/home/ashkin/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/platform-tools

# autorun
# firefox
#firefoxPid=`ps -ef|grep firefox|grep -v grep|awk '{print $2}'`
#if [ -n "$firefoxPid" ] ; then
#    echo "Firefox is running"
#else
#    sh -c "nohup firefox > /dev/null 2>&1 &"
#fi
```


## Shell

```Shell
// 打开 Apple Book iCloud 路径
open ~/Library/Mobile\ Documents/iCloud\~com\~apple\~iBooks/Documents/

// homebrew update
brew update --auto-update && brew upgrade && brew autoremove && brew cleanup --prune=all
```

## Python

```Python
// Python 启动服务器
python3 -m http.server
```