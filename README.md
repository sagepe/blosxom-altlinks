# Blosxom plugin - altlinks

This is a very simple plugin for the [Blosxom](http://blosxom.sourceforge.net/) weblog application written back in 2004. I've not used Blosxom for a long time and this repository is intended as an archive.

The information below is derived from the POD in-line in the plugin itself:

## Description

`altlinks` was designed to allow you to include alternate `<link>` tags in your HTML templates for syndication feeds that mirror a visitors position in the filesystem hierarchy.  That is, the `href` attribute will include the path of the document viewed, all the way down to the single file level.

I wrote this plugin because it always seemed to me that the root RSS feed wasn't really an "alternate" for a single entry page - especially as the root feed might not even include that entry any longer.  Also, since it is possible to subscribe to feeds for specific categories, supplying the correct information in the `<head>` of the HTML document seemed sensible.

## Installation

Simply drop altlinks into your plugins directory.

## Configuration

By default, the plugins assumes that you have flavours named `rss`, `rdf` and `atom`.  You can alter these assumptions by adjusting the variables at the top of the plugin (`$rss_flav`, `$rdf_flav` and `$atom_flav`) to point at the correct flavours.  There is nothing stopping you using the variables for different formats to those suggested by the variable names - you'll just have to remember what points where and adjust the `<link>`s in your HTML templates to match.

altlinks provides three variables for use in your templates: `$altlinks::alt_rss`, `$altlinks::alt_rdf`, and `$altlinks::alt_atom`.  Each contains the full path to a given feed for the page being viewed.  To use these, include a `<link>` in the `<head>` section of your HTML template for each alternate you want to point to, something like:

```
<link rel="alternate" type="application/rss+xml" href="$altlinks::alt_rss" />

<link rel="alternate" type="application/rdf+xml" href="$altlinks::alt_rdf" />

<link rel="alternate" type="application/atom+xml" href="$altlinks::alt_atom" />
```
## Changelog

Version `0.1` used hardcoded flavour names.

## Bugs

Currently `altlinks` only works for path-based URLs, date-based ones are ignored and the href attribute for the `<link>` will be formed from whatever path fragments there are in the requested URL.