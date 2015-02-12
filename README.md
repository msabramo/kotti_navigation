# kotti_navigation

[![PyPI](https://img.shields.io/pypi/v/kotti_navigation.svg?style=flat-square)](https://pypi.python.org/pypi/kotti_navigation/)
[![Downloads in the last month](https://img.shields.io/pypi/dm/kotti_navigation.svg?style=flat-square)](https://pypi.python.org/pypi/kotti_navigation/)
[![License](https://img.shields.io/pypi/l/kotti_navigation.svg?style=flat-square)](http://www.repoze.org/LICENSE.txt)
[![Build Status](https://travis-ci.org/Kotti/kotti_navigation.svg?branch=master)](https://travis-ci.org/Kotti/kotti_navigation)


This is an extension to [Kotti][1] that renders navigation displays in a choice of available locations for a Kotti website (top nav, left slot, right slot).


## Set up kotti_navigation

To activate kotti_navigation add the following entry, as with any add-on, to kotti.configurators of your .ini config file. ``kotti_navigation`` depends on [kotti_settings][2], so you have to add also an entry for this add-on. So the kotti.configurators part of your your ini file should include the following lines.

```ini
kotti.configurators =
    ...
    kotti_navigation.kotti_configure
    kotti_contentpreview.kotti_configure
```

## How to use it?

You have different settings to adjust ``kotti_navigation`` to your needs. You get the settings page on http://yourkottidomain.tdl/@@settings and you find it a link to `Settings` in the dropdown of menupoint `Administrator` of the editor bar. In the default no special navigation is activated and the default navigation bar from Kotti will be used.


![settings](https://raw.github.com/Kotti/kotti_navigation/master/docs/images/settings.png "Navigation Settings")

There are three locations are available::

* top (within and beneath the default nav toolbar)
* left (slot)
* right (slot)

For every location you have an own tab in the settings. There you can choose if the navigation is enabled for the location and how it will be displayed.
The following options are available.

### Display Types

With the display type you choose how your navigation will be rendered.

- Not enabled
  > As expected the widget will not be shown in the slot.
- Tree
  > The full tree is used for the navigation.
- Items
  > Only the the children of the current context are included.
- Menu
  > The navigation will be rendered as a dropdown menu.
- Breadcrumbs
  > Here the real breadcrumbs will be rendered, useful when you need it
    in another slot than usual.

For a typical website that has a tree navigation display in the left slot, you would configure for only the left location, and omit configuration for any other. But you are encouraged to play around with the possibilities.

### Options

The options are a multi selection box, so you can enable how much you want, however it will not always make sense to mix all of the options together.

- List
- Pills
- Tabs
  > These define the bootstrap classes that are used to render the navigation. It is recommended to only use one of them.
- Stacked
  > This makes your navigation stackable. Refer to the [bootstrap documentation](http://getbootstrap.com/components/#nav) for more information.
- Open all
  > This will be open all of your menu points no matter where your context is. This is useful if you plan to set up a menu via css or javascript, because all items in the site hierarchy are always included.
- With Dropdowns
  > tbd
- Show Menu
  > tbd
- Include Root
  > Indicate if the root object will be included on the top of the navigation and so an item showing the title of the root of the site is inserted as the first item for the display choices.
- Show hidden while logged in
  > With this option enabled items that are not included in the navigation for the user of the website are shown to the editor or admin.


### Include Content Types

Here you find a list of the content type names that are to be allowed in a given navigation display. Use this, for example, to have a nav tabs display in the top location, along with an images-only display in the right slot. The images-only nav display could be given a label such as "Images:" for clarity.

### Exclude Content Types

This is a list of the names of content types that are to be ignored in the navigation display. It is the opposite of the ``Include Content Types`` setting described above. It is commonly used to exclude the Image content type from a normal nav display, to avoid the "clutter" with listing images, which can be numerous. The same could be true for other content items, such as for a site that allows the Event content type
of kotti_calendar to be stored in various places in the site, and where events are wished to be shown only on calendar or event list displays.

### Label

The label is optional, but can provide clarification in some nav display cases.
It is positioned within the display in different ways, depending on display type. In a tree-type display (one of the "stacked" display choices), it is at the top of the display. The label is optional, but can provide clarification in some nav display cases. It is positioned within the display in different ways, depending on display type.

The current context will be indicated by the highlighting of the context menu item in the indented display. This is normally adequate. However, for extra clarity, or for some special reason, you may want to include the current context in the label, in a phrase such as "Current item: context", where the word ``context`` would be replaced by the actual context.title. To do this, include the actual word ``context`` in the label text, so `<context>` would become ${'<' + context.title '>'} in the template code.

[1]: http://pypi.python.org/pypi/Kotti
[2]: http://pypi.python.org/pypi/kotti_settings
