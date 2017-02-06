# newTools

## 《 AngularJS深度剖析与最佳实践》安装front-jet失败

作者雪狼已经给出了解决方案，地址估计学习这个的读者应该都能翻过去吧。
本人在此也写一下自己的安装经历吧。
我一开始买到书后就想安装front-jet，始终没有成功，之后再github上找源码无意间发现作者给出来解决方案。

一些读者反映安装FrontJet有困难，我做了一些改进，它支持在Node 5下运行。由于Node 5.x 版本的NPM工具有了显著提升，所以安装到一半儿被卡住等问题都解决了。请获取最新版FrontJet源码，并在它的目录下运行npm link。但是仍然需要翻墙，因为phantomjs的下载源被墙了。

部分书友反映安装front-jet失败，这是因为fj依赖了很多第三方库，安装时容易出现问题，特别是网络不好的时候。所以我制作了Windows下的离线安装包，链接: http://pan.baidu.com/s/1mgZ3FMK，密码: q5v5。先确保本地的NodeJS是4.x版本（注意：离线安装包不支持其它版本的NodeJS），然后把它解压到一个目录，然后把这个目录加入环境变量PATH中即可 —— 注意，添加完PATH之后要重新开cmd窗口才会生效。

如果安装后运行时出现The ‘libsass’ binding was not found错误，请进入node_modules/gulp-sass目录，然后运行npm rebuild node-sass即可。

1. 我就在家里的Win64位的笔记本上安装了nodejs4.4.7的64位版本，并且下载了百度云里面的front-jet离线包；
2. 安装完成后进入front-jet所在目录，运行 fj create BookForum，再进入BookForum文件夹运行fj serve时提示错误，就是作者提到的“The ‘libsass’ binding was not found错误”；
3. 此时安装作者给的解决方案：“请进入node_modules/gulp-sass目录，然后运行npm rebuild node-sass即可”，搞定此问题。
4. 运行fj serve还是出错，但是此时的错误就比较明显了，会有指引性提示，大致意思就是要你手动运行bower install。
5. 我就下载了bower和git（书中已经提到要按照git）在BookForum文件夹内运行bower init，填写了相关信息，然后运行bower install（亲测得先运行bower init，才行）。
6. 最后终于大功告成。********

2016-07-26_191444
我回单位电脑Win10 64位安装同样办法安装front-jet失败，可能跟win10系统有关。
于是我再次尝试直接用npm install -g fj安装，我的nodejs还是尝试离线版时安装的4.4.7的64位版本，期间提示需要下载phantomjs，为了节省时间，我自己下载了phantomjs，并将其添加至PATH环境变量。
再次运行npm install -g fj，等待运行，期间”D:\nodejs\node_global\node_modules\fj”里面生成不少文件，可是等待命令运行完成后，发现安装期间有不少错误，最后将”D:\nodejs\node_global\node_modules\fj”里面的文件基本都删完了。
于是我在

`   > node-sass@3.8.0 install  
    D:\nodejs\node_global\node_modules\fj\node_modules\gulp-sass\node_modules\node-sass
    > node scripts/install.js `  
按CTRL+C停止了进程，这样之前生成的文件是保住了，还没有来得及被删。  

fj
运行fj init，报出错误，提示用“This usually happens because your environment has changed since running `npm ins
tall`.
Run `npm rebuild node-sass` to build the binding for your current environment.”
于是运行npm rebuild node-sass，然后运行fj init就成功了
fj2

然后按照上面的4、5、6完成了front-jet的在线安装。