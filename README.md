
# Deeds.js

## What?
Deeds is a very simple client side Data Access Layer. An abstraction meant to reduce the boiler plate code associated with making ajax calls. Here is a very trivial example. An application defines several calls to the Middle-end which are grouped by the HTTP verb that they will use.

      var deed = new deeds({
        
        get: { // optional
          users: '/api/users/:partialname',
          apps: '/api/apps/:partialname'
        },
        
        post: { // optional
          users: '/api/users'
        }
        
      });

### Usage. Here is our above definition put to use...

      deed.get.users(

        { partialname: 'johnny' },

        function(error, response) {
          console.log(error || response);
        }

      );

### Here we have a more complex example...

      var deed = new deeds({
        
        get: { // optional
          users: '/api/users/:partialname',

          apps: '/api/apps/:partialname',
          appsBy: '/api/apps/:username',

          servers: '/api/servers',
          auth: '/api'
        },
        
        post: { // optional
          users: '/api/users'
        },
        
        delete: { // optional
          users: '/api/users/:username'
        }

      }).use({
        port: 8080, // optional 
        headers: { 'Accept': 'application/json' } // optional
      });

### An example of the above code in use...

      deed.get.users(

        { partialname: 'johnny' }, // optional

        { /*data*/ }, // optional

        function(xhr) { // optional
          xhr.setRequestHeader('authorization', 'Basic ' + encodeBase64('user:password'));
        },

        function(error, response) { // required
          console.log(error || response);
        }

      );
      
# Licence

(The MIT License)

Copyright (c) 2010 hij1nx <http://www.twitter.com/hij1nx>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.