# skipper-s3-resize

Based on SailsJS Skipper S3 adapter for receiving [upstreams](https://github.com/balderdashy/skipper#what-are-upstreams) with a twist: Images will be resized before uploading using GraphicMagick.

## Installation

1. First, make sure you have graphicmagick installed.

2. Install via npm:
```
$ npm install skipper-s3 --save
```

3. Also make sure you have skipper itself [installed as your body parser](http://beta.sailsjs.org/#/documentation/concepts/Middleware?q=adding-or-overriding-http-middleware).  This is the default configuration in [Sails](https://github.com/balderdashy/sails) as of v0.10.

4. You will now have the package installed.

## Usage
1. In Controller:
```javascript
  upload: function(req, res) {
    req.file('image').upload({
      adapter: require('skipper-s3-resize'),
      key: <YOUR_S3_KEY>,
      secret: <YOUR_S3_SECRET>,
      bucket: <YOUR_S3_BUCKET>,
      resize: {
        width: <WIDTH>,
        height: <HEIGHT>,
        options: <GRAPHICMAGICK_OPTIONS>
      }
    }, function(err, uploadedFiles) {
      if(err) return res.serverError(err);
        res.ok();
      });
    }
```

## Options
1. Refer [skipper documentations.](https://github.com/balderdashy/skipper#uploading-files-to-s3)