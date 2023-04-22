# imguiInMac
using imgui in Mac

imgui 选择其中的glfw + opengl3
# thirdlib
## glfw glew
使用cmake+make编译生成libglfw3.a和libGLEW.a

* glfw在mac中编译报"not return NSString"相关错误  
安装了xcode重启后解决

* 使用glew库确定增加了库文件和路径后，报
```
unresolved external symbol __imp__glewInit@
```
如果不定义GLEW_STATIC，那么所有函数符号都按照动态库方式声明和调用。需要加上宏定义。
```
#define GLEW_STATIC
```

* 使用glfw库确定增加了库文件和路径后，报奇怪的Cocoa等相关错误  
需要增加系统的framework库，在"/System/Library/Frameworks"目录下

# reference
[glfw](https://github.com/glfw/glfw)
[glew](https://github.com/nigels-com/glew/releases/download/glew-2.2.0/glew-2.2.0.zip)