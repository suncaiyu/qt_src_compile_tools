# qt_src_compile_tools
编译qt5.15的需要的工具

需要：
python 3(有的说3不行 要2.7.5以上，但是我用的3.10页正常编译)
perl 
ruby(说是需要，但是我好想没安装也成功了)

坑：我第一次编译的时候，直接在src目录下进行了cmake 但是最后 install的时候 G 了  报了目录名不合法的错误

所以最好建3个目录：
1. src -- 放源码
2. build -- 编译目录
3. install -- 安装目录

过程
1.cd 到 build
2. 我编的msvc版，所以打开vs自带的命令行工具  输入  "../qt-everywhere-src-5.15.1/configure.bat" -static -prefix "D:\qt5.15.1" -confirm-license -opensource  -debug-and-release -platform win32-msvc  -nomake examples -nomake tests  -plugin-sql-sqlite -plugin-sql-odbc -qt-zlib -qt-libpng -qt-libjpeg -opengl desktop -mp
适当修改，具体参数含义见https://doc-snapshots.qt.io/qt5-5.15/configure-options.html     -static是静态库   -shared是动态库  (因为浏览器模块一般来说是不需要的 qwebengine ，可以通过-skip qtwebengine 跳过，但是我失败了(摊手))
3. s上一步编译好makefile后   直接 jom -j xx或者nmake
4. jom -j xx install 或 nmake install


编译要好久  大概2h？    好在最后成功了   编译的库可以编译qt程序。
