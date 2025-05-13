# A simple sketchybar config for aerospace users!
![alt text](bar_img.png)
I couldn't find any resources for a simple sketchybar config that worked with aerospace. So this is what I came up with!

The styling is really ugly, i'm sorry. Hopefully that encourages you to tinker with the setup :p

anyways if you're looking for something more fleshed out:
[Here's my how current configuration looks](https://github.com/Kainoa-h/MacSetup)

## Credits:
I'm kinda new to shell scripting and all this stuff.
Here are the resources that helped me make this config besides the official [sketchybar](https://felixkratz.github.io/SketchyBar/config/bar) and [aerospace](https://nikitabobko.github.io/AeroSpace/guide) docs :p

 - [This github user's wayyyy more advanced sketchybar & aerospace setup](https://github.com/forteleaf/sketkchybar-with-aerospace)
 - [Josean Martinez's amazing guide for setting up sketchybar with yabai](https://www.josean.com/posts/sketchybar-setup)

## Aerospace:
### Getting it working:

If you already have an aerospace config or don't want to use mine, add the following into your `aerospace.toml` to trigger sketchybar & pass workspace data.
``` Shell
exec-on-workspace-change = ['/bin/bash', '-c',
    'sketchybar --trigger aerospace_workspace_change FOCUSED_WORKSPACE=$AEROSPACE_FOCUSED_WORKSPACE PREV_WORKSPACE=$AEROSPACE_PREV_WORKSPACE'
]
```



You should also add `--focus-follows-window` to the workspace change binds.
This forces the workspace to follow when a window is moved to another workspace. This will cause 'exec-on-workspace-change' to fire, keeping the bar updated.
Without this, when windows are moved to a new space, they won't appear in the bar until the bar is focused.
From the [Aerospace guide](https://nikitabobko.github.io/AeroSpace/commands#move-node-to-workspace):

> "Make sure that the window in question receives focus after moving. This flag is a shortcut for manually running aerospace-workspace/aerospace-focus after move-node-to-monitor successful execution."

``` toml
alt-shift-1 = 'move-node-to-workspace 1 --focus-follows-window'
alt-shift-2 = 'move-node-to-workspace 2 --focus-follows-window'
alt-shift-3 = 'move-node-to-workspace 3 --focus-follows-window'
alt-shift-4 = 'move-node-to-workspace 4 --focus-follows-window'
...
```

## Sketchybar
### Current Functionality:
 - Dynamically displays/hides active/inactive workspaces. (not working perfectly...)
 - Displays apps in each workspace
 - Displays total swap memory (updates every 20 seconds)

### Getting it working:
You will need to install a Nerd Font if you haven't already!
``` Shell
brew tap homebrew/cask-fonts
brew install font-hack-nerd-font
```

jq as well!
``` Shell
brew install jq
```

I used the SF font in my config so let's install that too! If you don't want to, that's fine as well. Just remeber to change the fonts used in `sketchybarrc`
```
brew install font-sf-pro
```

Lastly, you'll want to grab the [sketchybar app font](https://github.com/kvndrsslr/sketchybar-app-font/releases) and add it to your '~/Library/Fonts/' directory!
