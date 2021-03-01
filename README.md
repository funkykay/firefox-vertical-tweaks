# firefox-vertical-tweaks
**Firefox UI tweaks extending the 'Tree Style Tab'-Addon for optimizing vertical page size**

tested with macos (catalina/big sur)

## Screenshot
![Screenshot](/screenshot_2020-08-12_131154.png?raw=true "")

## Setup
- Open the your current Firefox Profile folder
    - Firefox Menu > Help > Troubleshooting Information > Profile Folder
- create a folder `chrome`
- go into created folder and paste `userChrome.css` file from this repostory
    - in console: `wget https://raw.githubusercontent.com/funkykay/firefox-vertical-tweaks/master/userChrome.css`
- activate custom stylesheets in Firefox:
    1. navigate firefox to `about:config`
    2. accept warning
    3. change toolkit.legacyUserProfileCustomizations.stylesheets flag to true
- *optional* condensed topbar: Firefox Menu > Customize Toolbar > Density (at the bottom bar) > Compact

*for detailed guide see: https://www.userchrome.org/how-create-userchrome-css.html*

## Features
### hide tabs on topbar
**Source:** forgotten
```css
#TabsToolbar {
    visibility: collapse;
}

#titlebar {
    visibility: collapse;
}
```

### hide header of 'Tree Style Tab'-Addon
**Source:** forgotten
```css
#sidebar-header {
    visibility: collapse !important;
}
```

### show bookmarks only in new Tab
**Source:** https://superuser.com/a/1520406/1208153
```css
#nav-bar:not(:focus-within) + #PersonalToolbar:not(:hover):not(:focus-within):not([customizing]) { 
    visibility: collapse; 
}
```

### disable urlbar from expanding on click
**Source:** https://support.mozilla.org/en-US/questions/1284030#answer-1304125
```css
#urlbar[breakout],
#urlbar[breakout][breakout-extend] {
  --urlbar-height: 28px !important;
  --urlbar-toolbar-height: 30px !important;

  width: 100% !important;
  top: calc((var(--urlbar-toolbar-height) - var(--urlbar-height)) / 2) !important;
  left: 0 !important;
}

#urlbar[breakout][breakout-extend] > #urlbar-input-container,
#urlbar-input-container {
  height: var(--urlbar-height) !important;
  width: 100% !important;
  padding-block: unset !important;
  padding-inline: unset !important;
  transition: none !important;
}

#urlbar[breakout][breakout-extend] > #urlbar-background {
  box-shadow: 0 1px 4px rgba(0,0,0,.05) !important;
  animation: none !important;
}
```
