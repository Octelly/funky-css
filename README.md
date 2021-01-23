# Funky CSS

![Tested Jellyfin version](https://img.shields.io/badge/Jellyfin-10.6.4-%2300A4DC)

A Jellyfin theme

## About

A theme that I use on my Jellyfin instance and some variants of it. If you have an ideas or stuff like that, submit an issue and I'll probably look at it eventually.

## How to use

1. log into Jellyfin with an admin account
2. open your dashboard
3. go to "General"
4. paste a CSS import link in the "Custom CSS" section

### Import links

A valid CSS import link links to any of the files in the ``variants`` directory in the root of this repo's ``main`` branch.

#### Examples

| Variant | Syntax |
| ------- | ------ |
| Default | ``@import url('https://raw.githubusercontent.com/Johnystar/funky-css/main/variants/default.css');`` |

## Updating the theme

Jellyfin always loads the theme directly from GitHub, nothing to worry about.

## Repository structure

| Directory | Purpose |
| --------- | ------- |
| ``variants`` | Stylesheets that you import into Jellyfin |