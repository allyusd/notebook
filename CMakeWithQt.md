[CMakeLists.txt](https://github.com/allyusd/cmake/edit/master/qt/CMakeLists.txt)

```
cmake_minimum_required (VERSION 2.8.12)
project (MyProject)

find_package(Qt5 COMPONENTS Core Widgets REQUIRED)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

add_library (${PROJECT_NAME}Lib
	mainwindow.h mainwindow.cpp mainwindow.ui)

target_link_libraries (${PROJECT_NAME}Lib Qt5::Widgets)

add_executable(${PROJECT_NAME} main.cpp resources/resources.qrc)
target_link_libraries (${PROJECT_NAME} ${PROJECT_NAME}Lib)
```

Don't forget CMAKE_PREFIX_PATH

[Build.bat](https://github.com/allyusd/cmake/blob/master/qt/Build.bat)

```
SET CMAKE_PREFIX_PATH=C:/Qt/5.7/msvc2015
  ...
```

Ref:

[Implementing Qt project through CMake](http://stackoverflow.com/questions/25989448/implementing-qt-project-through-cmake)

[CMake: Finding Qt 5 the “Right Way”](https://blog.kitware.com/cmake-finding-qt5-the-right-way/)

[Qt Documentation - CMake Manual](http://doc.qt.io/qt-5/cmake-manual.html)

[CMake 3.7 Documentation - cmake-qt](https://cmake.org/cmake/help/v3.7/manual/cmake-qt.7.html)

[USING CMAKE WITH QT 5](https://www.kdab.com/using-cmake-with-qt-5/)

[Default installation prefix QT5 / QT5 Widgets Ubuntu](http://askubuntu.com/questions/633826/default-installation-prefix-qt5-qt5-widgets-ubuntu)

[What package do I need to build a Qt 5 & CMake application?](http://askubuntu.com/questions/374755/what-package-do-i-need-to-build-a-qt-5-cmake-application)

[Add the installation prefix of “Qt5Widgets” to CMAKE_PREFIX_PATH](http://stackoverflow.com/questions/22215900/add-the-installation-prefix-of-qt5widgets-to-cmake-prefix-path)

[AUTORCC](https://cmake.org/cmake/help/v3.7/manual/cmake-qt.7.html#autorcc)

Todo:

[Automated translation management with Cmake and Qt5](http://stackoverflow.com/questions/19193121/automated-translation-management-with-cmake-and-qt5)

[Qt5LinguistTools macros](http://doc.qt.io/qt-5/cmake-manual.html#qt5linguisttools-macros)
