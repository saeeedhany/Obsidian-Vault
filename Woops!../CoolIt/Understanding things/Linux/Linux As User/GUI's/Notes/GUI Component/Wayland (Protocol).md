*So* What exactly is **Wayland** ?? (This answer from reddit).

Basic problem to solve: You have a screen and one application that draws on it. To make it more complicated you do not have only one but multiple applications, and you don't want them to fight over the same pixels.

The most simple solution is a file called /dev/fb0 (**[[Frame Buffer]]**). This is like a "jpeg" you write if you want something to appear on the screen. The problem is this only works if only one application with root permission tries it.

The solution you have one application that has root which draws onto the screen (let's call it X server) and applications connect with the server. The commands where designed to be simple and efficient on 1980's devices. Like draw image, draw rectangle, draw text with a bitmap font that can't be rescaled. The XServer does not determine the position of the windows, and doesn't draw window decorations like window close button etc. That's the responsibility of a window manager. Also instead of drawing directly on to the screen, shadow buffers can be used to composit the windows later, job of a **[[compositor]]**.

The problem now is, that there is no support 2D hardware acceleration and every vendor had it's own solution resulting in a lot of special "DDX"(Device Dependent X) drivers. But since the times of 3D acceleration X lost more and more of it's purposes. This is because devices turned away from DDX and fb to the more versatile DRM (Direct Rendering Manager) and away from draw rectangle to **[[Vulkan]]** that can do everything fancy. And as X (refers to [[XServer (Protocol)]] ) hat to add extensions for everything that people started wanting to do with their hardware, like video playback, or fast 3D games. X did less and less itself, to a point where on a modern system wit applications like Chrome and toolkits like GTK, X does nothing than connecting parts that could communicate directly.

That's where the idea of Wayland came into existence: merge the window manager and compositor into one application called Wayland compositor. And drop the X server completely since Vulkan (and DRM) does nowadays all abstraction over different hardware vendors.

An desktop environment is a collection of a window manager and compositor or a Wayland compositor and a set of default applications and the dock, file manager ... Wayland itself does nothing with GUI, but only defines an interface for the application to get the memory in which to draw the GUI.

Wayland is also concerned with keyboard, mouse, trackpad and touch input, but that's the boring part and simply maps to libinput.