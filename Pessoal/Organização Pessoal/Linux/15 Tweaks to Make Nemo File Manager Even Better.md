---

---
[https://itsfoss.com/nemo-tweaks/](https://itsfoss.com/nemo-tweaks/)

Nemo is the default file manager of the Cinnamon Desktop. You get it in Linux Mint and other distributions with the Cinnamon desktop.

It’s a powerful file manager with plenty of features you might not know. Some tweaks are hidden inside the Nemo settings while some require installing additional extension packages.

I have included commands for installing extensions for Ubuntu and Debian-based distributions.

***Note: Please don’t go and install all the extensions. Only use the ones you would use.***

## 1. Enable quick file preview

Nemo Preview is a cool feature that comes in handy if you want to peek into some files on the go. You can access the preview feature for images, audio, video, PDF, etc.

It also allows scrolling the documents in preview mode and adds a floating control with a seek par in audio/video preview.

File Preview in Nemo File Manager With Nemo Preview

![[file-preview-in-nemo-file-manager-with-nemo-preview.png]]

You can get the preview feature by installing the following extension:

```plain text
sudo apt install nemo-preview
```

Once installed, you may need to restart the Nemo file manager.

To activate the preview, **select the file and press the Space key**. Pressing the space key again will close the preview.

## 2. Click twice to rename

This is one of the iconic features of Nemo file manager, which is already offered in Dolphin File Manager of KDE, but absent in Nautilus of Gnome.

To enable this setting, you need to go to Edit > Preferences > Behaviour and toggle the option as shown below:

Click on File Name Twice to Rename It

![[click-on-file-name-twice-to-rename-it.png]]

Once done, you can now click twice on a file/folder and an inline rename option appears to rename the respective selection.

## 3. Bulk rename files

Nemo also offers a bulk rename feature that many Linux users are not aware of.

What you have to do is, select the files and select **rename** from the right click. You’ll get different kinds of options to tweak the names of the selected group of files.

Nemo File Manager Bulk Rename

![[nemo-file-manager-bulk-rename.png]]

You can find and replace, remove certain parts of the name among many other things.

## 4. Double click anywhere to go to the parent folder

This is rather an accessibility setting. Instead of pressing the back button or clicking on the places tree, you can simply double-click anywhere in the empty space in the window to go to the parent folder.

To enable this feature, go to Edit > Preferences > Behaviour and toggle on the option as shown in the screenshot below.

Double Click on Blank Area to go to Parent Folder

![[double-click-on-blank-area-to-go-to-parent-folder.png]]

## 5. Compress files and folders

This is not a secret really. Almost all file managers have this option as far as I know.

Right click on a file or folder and you get the Compress option to create an archive file.

Compress Option in Right Click Context Menu

![[compress-option-in-right-click-context-menu.png]]

You can choose between formats like .7z, .tar, .zip to .apk, .epub. etc. Some compression methods like epub requires their own defined formats to succeed.

Compress Options

![[compress-options.png]]

Some compression formats support password protection, encryption and splitting, as shown in the above screenshot.

If you did not find this option, you could install the package nemo-fileroller:

```plain text
sudo apt install nemo-fileroller
```

## 6. Configure the right-click context menu

By default, there are many options in the right-click context menu. If you are one of those users who want to control what appears on your right-click menu, this is the feature for you.

You can access this setting from Edit > Preferences > Context Menus:

Configure Right Click Context Menu

![[configure-right-click-context-menu.png]]

Here you can toggle on or off various options you want to appear when you right-click anywhere. You can now populate your right-click menu with features you use frequently.

## 7. Rotate and resize images with right click

To enable this feature, you need to install nemo-image-converter package.

```plain text
sudo apt install nemo-image-converter
```

Restart Nemo and you can access the additional options right within the right-click context menu.

Rotate or Resize Images in Nemo File Manager

![[rotate-or-resize-images-in-nemo-file-manager.png]]

## 8. Change folder colours and add emblems

The feature to change folder colour was preinstalled on my Linux Mint 21. To change individual folder colour, right-click on the file and change colour from the context menu.

Change Individual Folder Color

![[change-individual-folder-color.png]]

If you don’t see it, you can install the extension:

```plain text
sudo apt install folder-color-switcher
```

Another cool feature is to add emblems to files and folders. To give an emblem to a file or folder, right-click and go to the properties dialog box.

From this, select the emblems tab and add whatever emblem you like.

Select Emblems for Files or Folders

![[select-emblems-for-files-or-folders.png]]

If it’s not installed by default, you can install it by:

```plain text
sudo apt install nemo-emblems
```

## 9. Verify checksum of files

There are dedicated tools to [verify checksum of files in Linux](https://itsfoss.com/checksum-tools-guide-linux/). You can also check hashes in the Nemo file manager with nemo-gtkhash extension.

```plain text
sudo apt install nemo-gtkhash
```

Now quit nemo and re-open. Select the file to check hash and go to the **Digests** tab in properties.

Check Hash Checksum of File with Nemo GTKHash

![[check-hash-checksum-of-file-with-nemo-gtkhash.png]]

It will take some time to check the hash and a tick mark, as shown in the above screenshot, indicates a successful result.

## 10. Use advanced permissions in properties dialog box

Now, you can view amore detailed an an intuitive permission dialog box for folders and file. To get this, you need to go to Edit > Preferences > Display and toggle the button on as shown below:

Show Advanced Permission in Property Dialog Box

![[show-advanced-permission-in-property-dialog-box.png]]

Now, instead of the old, drop-down menu interface, you get a neat-looking permission manager with a toggle button interface and more options to tweak.

Edit Advanced Permissions in Property Dialog Box

![[edit-advanced-permissions-in-property-dialog-box.png]]

## 11. Embed a terminal

Fancy a terminal? You can get it right inside the Nemo file manager.

Each time you change directories, a cd command is initiated and the location in the embedded terminal is also changed.

To get this function, you need to install nemo-terminal package.

```plain text
sudo apt install nemo-terminal
```

Now restart Nemo and you get an embed terminal on the top side.

Nemo Embedded Terminal

![[nemo-embedded-terminal.png]]

## 12. Get the list of recently visited directories

There is the “Recent” option in the places section, where you can see the recently accessed files. But what about the recently visited folders?

In Nemo, on the top left, **right-click on the back arrow** to get the list of previously visited folders.

Right Click on Top Left Back Arrow to Access Recent Folders

![[right-click-on-top-left-back-arrow-to-access-recent-folders.png]]

## 13. Show the number of items in folders

You can show how many files and folders are inside a folder in Nemo File Manager.

Show Number of Items Inside Folder Using Nemo File Manager

![[show-number-of-items-inside-folder-using-nemo-file-manager.png]]

It is a built-in feature. Go to Edit > Preferences > Display and select Size as shown in the screenshot below:

Show Folder Item Count and File Sizes in Nemo Preferences

![[show-folder-item-count-and-file-sizes-in-nemo-preferences.png]]

## 14. Nemo media columns

This is a small addition, useful only if you use the ‘List View’ in Nemo. It provides additional column options in the list view.

Column items: Before and After

![[default-list-columns-available-in-nemo.png]]

To get this feature, you need to install nemo-media-columns:

```plain text
sudo apt install nemo-media-columns
```

More Columns View in Nemo List View

![[more-columns-view-in-nemo-list-view.png]]

## 15. Nemo Scripts and Actions (for expert users)

Here are a few advanced features that enhances the overall function of nemo file manager by adding user defined functions.

### Nemo Scripts

With this feature, users can create their own shell scripts for certain functionality they wish and embed them into the right-click context menu.

You need to save your shell scripts in ~/.local/share/nemo/scripts directory. With the help of tools like [zenity](https://help.gnome.org/users/zenity/stable/?ref=itsfoss.com), you can even give a GTK interface for your script.

Let me show an example.

Below is a script adding a color palette to select colour and copy the colour to [copyq clipboard manager](https://itsfoss.com/copyq-clipboard-manager/). Save the file with name Color in the above-mentioned directory and give it executable permission. Copyq and Zenity should be installed.

```plain text
#!/bin/bash
name=$(zenity --color-selection --show-palette --title Color\ Select)
copyq add $name
```

Nemo Scripts in Right Click Context

![[nemo-scripts-in-right-click-context.png]]

Color Select with Zenity

![[color-select-with-zenity.png]]

The selected color code will now be accessible from the clipboard.

### Nemo Actions

This is similar to Nemo Scripts. Here, you can define a script in the form of a key-value pair for additional functions over selected files.

The files should have extension `.nemo_action` and they should be located in `~/.local/share/nemo/actions`

Here is a snippet of code provided in the Linux Mint Community. It creates an option to reduce the image size by 50%.

Save this script as reduce_50.nemo_action in the above-mentioned directory and you will find the option in right-click context menu

```plain text
[Nemo Action]
Active=true
Name=Reduce Image 50%
Comment=Reduce the size of the image by 50%
Exec=ffmpeg -i %F -vf scale=iw/2:-1 %P/copy-50%f
Icon-Name=image
Selection=any;
Extensions=jpg;jpeg;png;bmp;gif;tiff;raw;
Terminal=true
```

Reduce Image by 50 Percent Context Menu Entry

![[reduce-image-by-50-percent-context-menu-entry.png]]

You can see the resultant file with the slightly modified name.

Image Reduced with Nemo Actions Result

![[image-reduced-with-nemo-actions-result.png]]

This way, you effectively enhance Nemo file manager functionality as per your requirement.

## More tweaks and extensions

Apart from numerous extensions, there are other built-in features in Nemo like integrations with cloud services, other handy right-click menu items etc.

It is not necessary for you to install and use all of the features mentioned above. You can handpick those that suit your needs.

You can also **toggle on/off any of the installed extensions** by going to Edit > Plugins (or Alt + P).

Access Plugins from Menu

![[access-plugins-from-menu.png]]

Here, you can manage your installed plugins, actions, scripts etc. This enables you to activate or deactivate certain features without the hassle of installing/uninstalling packages. Every feature can be toggled on or off as needed. Just restart Nemo to get the effect.

Plugins View and Manage in Nemo

![[plugins-view-and-manage-in-nemo.png]]

When we last published the [Nautilus tweak article](https://itsfoss.com/nautilus-tips-tweaks/), a few readers requested a similar one for Nemo. And hence this article came into existence.

[It's FOSSAbhishek Prakash](https://itsfoss.com/nautilus-tips-tweaks/)

I hope you find the tweaks interesting. If you have suggestions or questions, please leave a comment.