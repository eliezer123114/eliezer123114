## hola bienvenidos 
use strict';
/*global describe:true, it: true, after: true */
var nodemon = require('../../lib/'),
  path = require('path'),
  assert = require('assert');

describe('when nodemon runs (1)', function () {
  var tmp = path.resolve('test/fixtures/env.js');
  after(function (done) {
    // clean up just in case.
    nodemon
      .once('exit', function () {
        nodemon.reset(done);
      })
      .emit('quit');
  });

  it('should pass through environment values', function (done) {
    nodemon({ script: tmp, stdout: false, env: { NODEMON_ENV: 'nodemon' } }).on(
      'stdout',
      function (data) {
        assert(
          data.toString().trim() === 'nodemon',
          'NODEMON_ENV env value correctly set to "nodemon": ' + data.toString()
        );
        nodemon
          .once('exit', function () {
            nodemon.reset(done);
          })
          .emit('quit');
      }
    );
  });
});

<!--
**eliezer123114/eliezer123114** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you 
- 🌱 I’m currently l
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
