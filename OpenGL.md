## OpenGL 基本概念

### 什么是OpenGL

OpenGL是一个由[Khronos组织](http://www.khronos.org/)制定并维护的规范(Specification)，OpenGL规范严格规定了每个函数该如何执行，以及它们的输出值。至于内部具体每个函数是如何实现(Implement)的，将由OpenGL库的开发者自行决定，实际的OpenGL库的开发者通常是显卡的生产商

### OpenGL的对象

在OpenGL中一个对象是指一些选项的集合，它代表OpenGL状态的一个子集，每一个对象用一个无符号整型标记

常见的对象:

顶点数组对象 VAO	顶点缓冲对象 VBO	索引缓冲对象 EBO/IBO

对象的一般使用方法:

```C++
// 创建对象
unsigned int objectId = 0;
glGenObject(1, &objectId);
// 绑定对象至上下文
glBindObject(GL_WINDOW_TARGET, objectId);
// 设置当前绑定到 GL_WINDOW_TARGET 的对象的一些选项
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_WIDTH, 800);
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_HEIGHT, 600);
// 将上下文对象设回默认
glBindObject(GL_WINDOW_TARGET, 0);
```

### OpenGL的上下文

OpenGL自身是一个巨大的状态机(State Machine)：一系列的变量描述OpenGL此刻应当如何运行。OpenGL的状态通常被称为OpenGL上下文(Context)。我们通常使用如下途径去更改OpenGL状态：设置选项，操作缓冲。最后，我们使用当前OpenGL上下文来渲染。

一般可以使用第三方库来创建OpenGL上下文，例如 GLFW, GLEW, glut, freeglut

创建上下文的伪代码(pseudocode)

```C
#include <libraryheaders>
int main()
{
    createWindow(title, width, height);
    createOpenGLContext(settings);
    while (windowOpen)
    {
        while (event = newEvent())
            handleEvent(event);
        updateScene();
        drawGraphics();
        presentGraphics(); //更换缓冲
    }
    return 0;
}
```



## 参考网站

https://learnopengl-cn.github.io/

https://open.gl/

https://learnopengl.com/

https://antongerdelan.net/opengl/

https://www.khronos.org/opengl/

https://www.opengl.org/