## Welcome to cannery-adapter

The base adapter for [Cannery](http://github.com/Aloompa/cannery).

## API

The Cannery Adapter is meant to be extended. There are just a handful of methods that can be overwritten to allow you to get and set data from whatever storage mechanism you like.

Adding an adapter to you model is as trivial as adding it as a static property to your model:

```
const Cannery = require('cannery');
const CanneryAdapter = require('cannery-adapter');

class User extends Cannery.Model {

    static adapter = CanneryAdapter;

    getFields () {
        return {
            // ...
        };
    }

}

module.exports = User;
```

### Methods

The base Cannery Adapter is an extendable class that can be used to create various strategies for retrieving and setting data. We plan to open-source many of our adapters for data sources like Ajax, WebSockets, Mocking, MongoDB, etc, but we wrote the adapter in such a way that it is pluggable and intended to be overridden with custom logic for specific use-cases. 

Every Cannery adapter has the following methods:

##### create(data)

Send data to a data store to get created. This must accept an object to send to the data store.

```
create (data) {
    return new Promise((resolve, reject) {
        // Save the data and resolve or reject the promise
    });
}
```

Returns: A promise, which resolves with the newly created data

##### destroy(id)

Remove data from a data store.

```
destroy (id) {
    return new Promise((resolve, reject) {
        // Delete the data and resolve or reject the promise
    });
}
```

Returns: A promise

##### findAll(query)

Find all of the data for a model.

```
findAll ({ page, per }) {
    return new Promise((resolve, reject) {
        // Retrieve the data and resolve or reject the promise
    });
}
```

Returns: A promise with an array of data

##### findOne(id)

Find one record.

```
findOne (id) {
    return new Promise((resolve, reject) {
        // Retrieve the data and resolve or reject the promise
    });
}
```

Returns: A promise with an object of data

##### update(id, data)

Updates the data for a model

```
update (id, data) {
    return new Promise((resolve, reject) {
        // Save the data and resolve or reject the promise
    });
}
```

Returns: A promise with the object of updated data

## Contributing

We encourage you to contribute to cannery-adapter by submitting bug reports and pull requests through [Github](http://github.com).

## License

cannery-adapter is released under The [MIT License](http://www.opensource.org/licenses/MIT) (MIT)

Copyright (c) [2015] [Aloompa LLC]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
