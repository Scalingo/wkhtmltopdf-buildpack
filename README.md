# wkhtmltopdf Buildpack

> [!WARNING]
> This repository has been deprecated and archived.
> Please use [Puppeteer](https://doc.scalingo.com/languages/nodejs/puppeteer) and the [`pdf`](https://pptr.dev/api/puppeteer.page.pdf) method instead.

This is a [buildpack][0] for bundling a compatible [wkhtmltopdf][1] binary with
your environment.

## Versions

* Buildpack:   `0.3`
* wkhtmltopdf: `0.12.6-1` by default

## Usage

[Add this buildpack][2] to your Scalingo application to install the `wkhtmltopdf`
and `wkhtmltoimage` binaries, and the corresponding library `libwkhtmltox`.
You need to setup your application to use a multi-buildpack environment.
Then, your application need both the wkhtmltopdf buildpack and the one for
the technology you use in your application. Here is an example using the Ruby buildpack:

```bash
$ scalingo env-set 'BUILDPACK_URL=https://github.com/Scalingo/multi-buildpack.git'
$ echo 'https://github.com/Scalingo/wkhtmltopdf-buildpack' >> .buildpacks
$ echo 'https://github.com/Scalingo/ruby-buildpack' >> .buildpacks
$ git add .buildpacks
$ git commit -m 'Add multi-buildpack'
```

### Other versiosn

If you want to use a `wkhtmltopdf` version other than 0.12.6-1, set
`WKHTMLTOPDF_VERSION`:

```bash
scalingo env-set WKHTMLTOPDF_VERSION="0.12.3"
```

As the distribution method for wkhtmltopdf has changed, you must also use a
specific version of the buildpack. So modify your `.buildpacks` to reference
the buildpack with a specific tag:

```
https://github.com/Scalingo/wkhtmltopdf-buildpack#v0.12.3
```

And commit this file.

## Troubleshooting

If you run into issues when trying to deploy with this buildpack, make sure your
app is running on the stack `scalingo-18`, `scalingo-20` or `scalingo-22`. You can check this
with:

```bash
$ scalingo apps-info
```

[0]: http://doc.scalingo.com/buildpacks/
[1]: http://wkhtmltopdf.org/
[2]: https://doc.scalingo.com/platform/deployment/buildpacks/multi
