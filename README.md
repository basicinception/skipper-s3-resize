# skipper-s3-resize
## Installation

1. First, make sure you have graphicmagick installed.
2. To use skipper-s3-resize module, simply paste skipper-s3-resize folder to any folder accessible by the server.
2. For example, paste the package inside appRoot > private
    ```
    - app.js
    - node_modules
    ...
    ...
    - private
    -- skipper-s3-resize
    --- package.json
    --- index.js
    ```
3. Then, edit your project ``package.json`` as following
   ``` javascript
     "dependencies": {
       "skipper-s3-resize": "file:./private/skipper-s3-resize"
     }
   ```
4. Run ``npm install``.
5. You will now have the package installed.

## Usage
1. In Controller:
   ```javascript
   upload: function(req, res) {
     req.file('image').upload({
       adapter: require('skipper-s3-resize'),
       key: <YOUR_S3_KEY>,
       secret: <YOUR_S3_SECRET>,
       bucket: <YOUR_S3_BUCKET>
     }, function(err, uploadedFiles) {
        if(err) return res.serverError(err);
        res.ok();
     });
   }
   ```

## Options
1. Refer [skipper documentations.](https://github.com/balderdashy/skipper#uploading-files-to-s3)