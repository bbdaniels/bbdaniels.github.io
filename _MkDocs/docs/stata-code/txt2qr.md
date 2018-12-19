# QR codes

Making QR codes with Stata is now easy! Here's an example using `txt2qr`:

```stata
txt2qr this is a test using "test.png", replace
```

![Making QR codes with Stata](/img/txt2qr.png)

txt2qr saves a QR code containing text to the location specified in using. The file
extension .png is recommended. Spaces and special characters are not currently supported in
text. Internet connection is required.

`txt2qr` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/txt2qr). Submit bugs and feature requests [here](https://github.com/bbdaniels/txt2qr/issues). If you like `txt2qr`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
