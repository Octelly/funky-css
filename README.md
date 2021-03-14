# Funky CSS

![Tested Jellyfin version](https://img.shields.io/badge/Jellyfin-10.7.0-%2300A4DC)

A Jellyfin theme

## About

A theme that I use on my Jellyfin instance and some variants of it. If you have an ideas or stuff like that, submit an issue and I'll probably look at it eventually.

## How to use

1. log into Jellyfin with an admin account
2. open your dashboard
3. go to "General"
4. paste a CSS import link in the "Custom CSS" section

### Import links

A valid CSS import link links to any of the files in the ``variants`` directory in the following format:

```css
@import url('https://jf-funky-css.johnystar.moe/variants/[FILENAME].css');
```

#### Examples

| Variant | Syntax |
| ------- | ------ |
| Default | ``@import url('https://jf-funky-css.johnystar.moe/variants/default.css');`` |

### When behind an Nginx reverse proxy

If the theme isn't working for you and you have Jellyfin set up behind an Nginx reverse proxy according to [Jellyfin's docs](https://jellyfin.org/docs/general/networking/nginx.html), here's how to fix the problem.

In your Nginx configuration file, there should be a line starting with ``add_header Content-Security-Policy``. This line describes, which sources should be treated as trusted, so that the browser doesn't load any content from potentially unsafe sources.

By default, this line doesn't include this repository. You can fix this, by appending ``https://jf-funky-css.johnystar.moe`` to the ``style-src`` section.

So, for example, if your configuration currently looks like this:

```
add_header Content-Security-Policy "default-src https: data: blob:; style-src 'self' 'unsafe-inline'; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com/iframe_api https://s.ytimg.com; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'";
```

then you want to change it to this:

```
add_header Content-Security-Policy "default-src https: data: blob:; style-src 'self' 'unsafe-inline' https://jf-funky-css.johnystar.moe; script-src 'self' 'unsafe-inline' https://www.gstatic.com/cv/js/sender/v1/cast_sender.js https://www.youtube.com/iframe_api https://s.ytimg.com; worker-src 'self' blob:; connect-src 'self'; object-src 'none'; frame-ancestors 'self'";
```

Special thanks to [this explanation](https://github.com/CTalvio/Monochromic#using-with-reverse-proxy) on how to deal with this problem and [Mozilla's Web Docs explaining CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP).

#### Security note

By applying this fix, you're allowing any CSS files from GitHub to be loaded, which could theoretically be dangerous (although unlikely). Please note, that I will not take any responsibility for anything you do that goes against [Jellyfin's official documentation](https://jellyfin.org/docs/general/networking/nginx.html) on this matter.

## Updating the theme

Jellyfin always loads the theme directly from GitHub, nothing to worry about.

## Repository structure

| Directory | Purpose |
| --------- | ------- |
| ``variants`` | Stylesheets that you import into Jellyfin |
