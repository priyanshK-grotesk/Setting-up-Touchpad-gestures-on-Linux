# Setting-up-Touchpad-gestures-on-Linux
# **Setting up Touchpad gestures on Linux**

Let’s admit it; Touchpad gestures have always been a nightmare for Linux users for ages. If you have ever used a Macbook or Windows 10 laptop with a compatible touchpad, you know what I’m talking about. Three-finger swipe, to switch between different application windows, to Four finger swipes, to switch between different workspace, It’s beautiful and hella productive at the same time.

[https://miro.medium.com/v2/resize:fit:700/0*zLzUtNrrPbS8injU](https://miro.medium.com/v2/resize:fit:700/0*zLzUtNrrPbS8injU)

Photo by [Sergey Zolkin](https://unsplash.com/@szolkin?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

Unfortunately, these gestures are not available by default on major Linux distributions, and even though there are many alternatives available, they require a lot of work for installation and that pain is unbearable. 🙄

> Fortunately, I recently came across one of the best gesture alternative a.k.a. Touchégg, in terms of how closely it resembles the gesture support of windows or Mac. I’ve used libinput gestures and Fusuma in the past but wasn’t happy with some of the features. Not only does Touchégg provide a beautiful user experience but it also lets you define separate gestures for specific applications. For e.g. you can set up four fingers swipe left to go back to the previous page on chrome/firefox and four fingers swipe right to go to the forward page.
> 

I’ve already configured these setting and attached at the bottom of this page; you can copy, paste and enjoy.

“[Touchégg](https://github.com/JoseExposito/touchegg) is an app that runs in the background and transforms the gestures you make on your touchpad into visible actions in your desktop. For example, you can swipe up with 3 fingers to maximize a window or swipe left with 4 fingers to switch to the next desktop. Many more actions and gestures are available, and everything is easily configurable.”

Here are some working examples from the official GitHub repo :

![https://miro.medium.com/v2/resize:fit:700/1*XIkYexe6ceCy6KNFZcYs7g.gif](https://miro.medium.com/v2/resize:fit:700/1*XIkYexe6ceCy6KNFZcYs7g.gif)

3 fingers Pinch

![https://miro.medium.com/v2/resize:fit:700/1*bSH0WoVhorvIY01WTV72uQ.gif](https://miro.medium.com/v2/resize:fit:700/1*bSH0WoVhorvIY01WTV72uQ.gif)

4-fingers swipe down to show desktop

Although the app currently is not GUI based(You have to change it using a text editor), it provides the best experience so far. So, without further ado, Let’s get into it.

# **Installation**

## **Ubuntu, Debian and derivatives**

Download the `.deb` package and install it. Double click on the package may work, otherwise install it from the terminal:

You can download one of the recent releases from here: [https://github.com/JoseExposito/touchegg/releases](https://github.com/JoseExposito/touchegg/releases)

```
$ cd ~/Downloads # Or to the path where the deb package is placed at
$ sudo apt install ./touchegg_*.deb # Install the package
```

## **Red Hat, Fedora, CentOS and derivatives**

Download the `.rpm` package and install it. Double click on the package may work, otherwise install it from the terminal:

You can download one of the recent releases from here: [https://github.com/JoseExposito/touchegg/releases](https://github.com/JoseExposito/touchegg/releases)

```
$ cd ~/Downloads # Or to the path where the rpm package is placed at
$ sudo yum localinstall touchegg-*.rpm # Install the package
```

## **Arch Linux, Manjaro and derivatives**

Install the `touchegg` package from [AUR](https://aur.archlinux.org/packages/touchegg/).

After the installation is done, you can run Touchégg manually by running the command `touchegg` in the terminal, or you can reboot to get started.

![https://miro.medium.com/v2/resize:fit:700/1*ckSdizQgwsLAjBKIdThwvA.png](https://miro.medium.com/v2/resize:fit:700/1*ckSdizQgwsLAjBKIdThwvA.png)

You can also run it from Start Menu:

![https://miro.medium.com/v2/resize:fit:700/1*-qUKZYjgqeTsaOKFamR8Zg.png](https://miro.medium.com/v2/resize:fit:700/1*-qUKZYjgqeTsaOKFamR8Zg.png)

Here comes the fun part ;)

# **Configuration**

Start by copying the default configuration from `/usr/share/touchegg/touchegg.conf` to `~/.config/touchegg/touchegg.conf`. You can do it using your file manager or by running this command in your terminal:

```
mkdir -p ~/.config/touchegg && cp -n /usr/share/touchegg/touchegg.conf ~/.config/touchegg/touchegg.conf
```

Now open `~/.config/touchegg/touchegg.conf` with your favourite text editor and add the gesture of your choice. You can refer the official documentation to set different gestures [here](https://github.com/JoseExposito/touchegg).

Touchegg already comes with pretty good built-in gestures, and you may not need to change it, but I liked the three fingers swipe to switch between my running applications (Alt+Tab), so I replaced it, you can do so by replacing the three fingers swipe left and right part with the following code :

```
<gesture type="SWIPE" fingers="3" direction="LEFT">
  <action type="SEND_KEYS">
    <repeat>true</repeat>
    <modifiers>Alt_L</modifiers>
    <keys>Shift_L+Tab</keys>
    <decreaseKeys>Tab</decreaseKeys>
  </action>
</gesture>

<gesture type="SWIPE" fingers="3" direction="RIGHT">
  <action type="SEND_KEYS">
    <repeat>true</repeat>
    <modifiers>Alt_L</modifiers>
    <keys>Tab</keys>
    <decreaseKeys>Shift_L+Tab</decreaseKeys>
  </action>
</gesture>
```
