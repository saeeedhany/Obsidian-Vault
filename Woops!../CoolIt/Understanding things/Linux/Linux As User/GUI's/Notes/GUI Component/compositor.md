This actually mean -> *a UI component that applies visual effects to windows before they are rendered on-screen*

*So* **What really are Compositors**

A compositor is a software which interacts with the window system as well as graphics in Linux to produce:

- Transparency in windows
- Transition animations
- Drop shadows around windows which give them a 3D effect
- V sync: Waits for the display to update before updating the display

With Compositor -> 
![[img1.png]]

Without compositor -> 
![[img2.png]]
As you can see, using compositors in a Linux desktop environment adds flavour to the aesthetics. Now let us see how they work.

**How Compositors Work**..
> The compositer causes an entire sub-tree of a window hierarchy to be rendered to an off-screen buffer. Applications can then take the contents of that buffer and do whatever they like.

![[img3.png]]

The off-screen buffer can be automatically merged into the parent window or merged by external programs, called compositing managers. Maintaining a buffer like this makes it easy to add additional frames during a window state change, such as fade-in and fade-out animations. Each frame of each running application goes through the compositor.

![[img4.png]]

### When to use a Compositor

A compositor should be used if there is a need of transparency, transition animations, v-sync and similar aesthetic features. Note that most desktop environments (like gnome) come with their own integrated compositors. Even some window managers like Compiz, Enlightenment, KWin, Marco, Metacity, Muffin, Mutter, Xfwm, do compositing on their own.

You would need to install a compositor separately if you are using a minimalistic desktop environment of window manager such as dwm, i3 or awesome. In such a case, since the environment is bare-bones (in the order of 1 to 5 megabytes), it is not shipped with a compositor off the shelf. In such cases, compositors like _compton_ or _picom_ can be used.

### When NOT to use a Compositor

The mechanism behind a compositor revolves around maintaining an off-screen buffer and passing that around different windows. While this might add a lot of effects to your window manager or desktop environment, it is NOT ideal during gaming, where it causes latency.

While gaming, not using a compositor might lead to the lack of v-sync (unless you turn v-sync on in-game) and a lot of screen tearing, but it does away with latency between frames. I would recommend turning the compositor off while gaming. The drawbacks can be avoided if hardware V-sync is used, but it requires altering the X11 config for synchronization at a graphics driver level. Specifically, enabling the **ForceFullCompositionPipeline** option for use with nvidia graphics (and **TearFree** option in the case of Intel) . In such a case, the compositor would not have to be turned off while gaming since v-sync will be offloaded to the graphics driver instead of the compositor itself. This would of course require the v-sync in the compositor to be turned off.