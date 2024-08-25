<h1 align="center">heroku-24-buildpack-wkhtmltopdf</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

## 📝 Table of Contents

- [About](#about)
- [Feature](#feature)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Acknowledgements](#acknowledgement)
- [License](#license)
- [Changelog](#changelog)


##  About <a name = "about"></a>

This buildpack downloads and extracts the
[wkhtmltopdf](https://wkhtmltopdf.org/) binaries and works on the `heroku-24` stack only.

- This buildpack downloads wkhtmltopdf v0.12.6.1-2 for the `heroku-24` stack.
- This buildpack can bypass stack detection if the url to the wkhtmltopdf binary is provided through Aptfile.

## Changelog <a name = "changelog"></a>
- v1.0 (initial release)
  - Support for `heroku-24`
  - Support for [Aptfile](#aptfile)

## Features <a name = "feature"></a>
- Downloads wkhtmltopdf binaries from [wkhtmltopdf.org](http://wkhtmltopdf.org)
- It does not add new environment variables or shell scripts.
- Tested on `heroku-24` stack images.
- It allows you to specify a custom or the latest version of wkhtmltopdf package for your app on Heroku. [Aptfile](#aptfile).

## Getting Started <a name = "getting_started"></a>
Just add the buildpack to your heroku app by executing:

```bash
heroku buildpacks:add https://github.com/Launch-Engine/heroku-24-buildpack-wkhtmltopdf.git
```

You can also force this buildpack to be the first Heroku process by using the
`--index` option:

```bash
heroku buildpacks:add --index=1 https://github.com/Launch-Engine/heroku-24-buildpack-wkhtmltopdf.git
```
### Aptfile(Optional) <a name="aptfile"></a>
To use a specific version of the wkhtmltopdf binary for your app on Heroku, you can include an `Aptfile` in the parent directory of your app. This file should contain the latest or custom download URL for the binary.

By including the `Aptfile`, you can bypass Heroku's stack detection and ensure that the correct version of wkhtmltopdf is downloaded during the build process.

Here are the steps to include an Aptfile in your app:

- Create a file named "Aptfile" in the parent directory of your app.
- Add the download URL for the version of wkhtmltopdf that you want to use to the Aptfile.
- Commit the Aptfile to your app's Git repository.
- Push the changes to Heroku.
- Once you've completed these steps, Heroku will use the specified version of wkhtmltopdf during the build process for your app.

### Warning: When using an Aptfile to specify the version of wkhtmltopdf for your app on Heroku, it's important to note that the Aptfile bypasses stack detection. This means that you need to make sure you are using the correct binary version for your Heroku stack.

## Usage <a name="usage"></a>

The binaries `wkhtmltopdf` and `wkhtmltoimage` will be available on `/app/bin`,
you can just execute `/app/bin/wkhtmltopdf ` and `/app/bin/wkhtmltoimage`  from your app.


## Acknowledgements <a name = "acknowledgement"></a>

- All thanks to [heroku-buildpack-apt](https://github.com/ddollar/heroku-buildpack-apt) project.

- This is a fork of https://github.com/RohanDebroy/heroku-buildpack-wkhtmltopdf, and was made to only support the `heroku-24` stack.

## License <a name="license"></a>
MIT
