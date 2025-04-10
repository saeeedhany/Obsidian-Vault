a tiling window manager splits your screen up like a grid and every window goes into a tile, unlike a floating window manager (which you’re more familiar with from other DEs) where every window is a floating container that can move totally freely and overlap other windows. a window manager is just that, it manages windows so if you want notifications, a status bar, etc you need other pieces of software to set that up (check other peoples configs on stuff like [r/unixporn](https://www.reddit.com/r/unixporn/) and see what else they use to make a full environment)

a dynamic window manager does the managing mostly automatically, it decides based on an algorithm how to split up the screen for you, in a manual window manager like i3 you divide up the screen and place windows yourself

finally [[Wayland (Protocol)]] is a display protocol. right now the long term de facto is x11([[XServer (Protocol)]]) but for security/technological reasons people are moving on from x11 to the newer wayland (you may have bugs on wayland it’s new and shiny but also new and lacking polish in some areas). the biggest difference in use for me at least is that with the wayland protocol the displaying of windows is handled by a compositor, whereas on x11 you would add a compositor on top of the display server. what a compositor does is some extra window processing which makes it possible to add the effects like animations, transparency, blur, etc. i wouldn’t worry too much about the technical side just know that a compositor makes your windows look cool and a display server allows applications to render on the screen.

**Other Response..**

So, you're currently using Gnome, which is a Desktop Environment - basically, a collection of several components to make your desktop work. This includes your Window Manager, as well as a number of other components and application designed to work together, such as screen lockers, wallpaper managers, panels etc.

The fun thing about Linux, is that you have the option of rolling your own DE, so to speak. That means you have the freedom to choose these individual components to make a system completely tailored to your needs. One of the most notable components of a standard DE is the Window Manager - that governs how your windows are set up, decorated, as well as animations and more.

Gnome's WM - Mutter - is a classic 'stacking window manager' - similar to what is used by Windows and macOS. However, there are other types of window managers, one of the most common being a 'tiling' window manager.

With a tiling WM, instead of a window just showing up on screen without any organization, it is automatically sized to the tiling screen. So, if you do not have any apps open, opening a new app will take advantage of all of the available space. But what happens when you want to open a second application? Now, the already open application will take up half of your screen, and the new app will take up the other half.

This is where the use of 'workspaces' comes in. If you've used macOS, then you may be familiar with the concept, it's a number of virtual 'desktops' that can hold open apps in whatever size you want.

That's a tiling window manager. the 'dynamic' part just means that the WM (in this case Hyprland) will decide how to arrange and size more apps as you open them on the screen, as opposed to manually dialling in the size. Hope that helps!

Please bear in mind this is something of a simplification to give you the brief overview - some details aren't 100% accurate but should at least give you enough of an idea to understand the concept.

#reddit
