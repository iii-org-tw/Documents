# Numpy.quantile
**numpy.quantile(a, q, axis=None, out=None, overwrite_input=False, interpolation='linear', keepdims=False, w=None)**

Compute the weighted q-th quantile of the data along the specified axis.

**Parameters**
- **a : array_like**
Input array or object that can be converted to an array.

- **q : array_like of float**
Quantile or sequence of quantiles to compute, which must be between 0 and 1 inclusive.

- **w : array_like, optional**
All weight value should be positive.
`w` must have the same shape with `a` or be a 1d array for broadcast.
When `w` is a 1d array, `axis` should be an `int` or `None` and
`w.size == a.shape[axis]` or `w.size == a.size`.
If `w` is set to `None`, it is equal to calling original np.quantile.

- **axis : {int, tuple of int, None}, optional**
Axis or axes along which the quantiles are computed. The default is to compute the quantile(s) along a flattened version of the array.

- **out : ndarray, optional**
Alternative output array in which to place the result. It must have the same shape and buffer length as the expected output, but the type (of the output) will be cast if necessary.

- **overwrite_input : bool, optional**
If True, then allow the input array a to be modified by intermediate calculations, to save memory. In this case, the contents of the input a after this function completes is undefined.

- **interpolation : {‘linear’, ‘lower’, ‘higher’, ‘midpoint’, ‘nearest’}**
This optional parameter specifies the interpolation method to use when the desired quantile lies between two data points ```i < j```:
    >linear: ```i + (j - i) * fraction```, where ```fraction``` is the fractional part of the index surrounded by ```i``` and ```j```.  
    >lower: ```i```.  
    >higher: ```j```.  
    >nearest: ```i``` or ```j```, whichever is nearest.  
    >midpoint: ```(i + j) / 2```.  

- **keepdims : bool, optional**
If this is set to True, the axes which are reduced are left in the result as dimensions with size one. With this option, the result will broadcast correctly against the original array a.

**Returns**
- **quantile : scalar or ndarray**
If q is a single quantile and axis=None, then the result is a scalar. If multiple quantiles are given, first axis of the result corresponds to the quantiles. The other axes are the axes that remain after the reduction of a. If the input contains integers or floats smaller than **float64**, the output data-type is **float64**. Otherwise, the output data-type is the same as that of the input. If out is specified, that array is returned instead.

**Examples**
```sh
>>> a = np.array([[10, 7, 4], [3, 2, 1]])
>>> a
array([[10,  7,  4],
       [ 3,  2,  1]])
>>> np.quantile(a, 0.5)
3.5
>>> w = np.array([[1, 2, 3], [3, 2, 1]])
>>> np.quantile(a, 0.5, w=w, axis=0)
array([3, 4.5, 4])
>>> w = np.array([1, 2, 3])
>>> np.quantile(a, 0.5, w=w, axis=1)
array([5.5, 1.5])
>>> np.quantile(a, 0.5, w=w, axis=1, keepdims=True)
array([[5.5],
       [1.5]])
>>> m = np.quantile(a, 0.5, axis=0)
>>> out = np.zeros_like(m)
>>> np.quantile(a, 0.5, axis=0, out=out)
array([6.5, 4.5, 2.5])
>>> m
array([6.5, 4.5, 2.5])
>>> b = a.copy()
>>> np.quantile(b, 0.5, axis=1, overwrite_input=True)
array([7.,  2.])
>>> assert not np.all(a == b)
```
# R wtd.quantile
**wtd.quantile (x, q, na.rm = FALSE, weight=FALSE)**

Compute the weighted q-th quantile of the data.

**Parameters**

- **x :**
    Vector of data, same length as weight.
- **q :**
    Quantile or sequence of quantiles to compute, which must be between 0 and 1 inclusive.
- **na.rm :**
    Logical: Should NAs be stripped before computation proceeds?
- **weight :**
    Vector of weights

**Returns**
    Returns an empirical q quantile from a weighted sample.
    
**Examples**
```sh
> require(Hmisc)
> data <- c(1,2,3)
> weights<- c(3, 2, 1)
> wtd.quantile(data, weights=weights, probs=0.5)
50%
1.5
```
# New Features!

  - Import a HTML file and watch it magically convert to Markdown
  - Drag and drop images (requires your Dropbox account be linked)


You can also:
  - Import and save files from GitHub, Dropbox, Google Drive and One Drive
  - Drag and drop markdown and HTML files into Dillinger
  - Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions that people naturally use in email.  As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Tech

Dillinger uses a number of open source projects to work properly:

* [AngularJS] - HTML enhanced for web apps!
* [Ace Editor] - awesome web-based text editor
* [markdown-it] - Markdown parser done right. Fast and easy to extend.
* [Twitter Bootstrap] - great UI boilerplate for modern web apps
* [node.js] - evented I/O for the backend
* [Express] - fast node.js network app framework [@tjholowaychuk]
* [Gulp] - the streaming build system
* [Breakdance](https://breakdance.github.io/breakdance/) - HTML to Markdown converter
* [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

### Installation

Dillinger requires [Node.js](https://nodejs.org/) v4+ to run.

Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

### Plugins

Dillinger is currently extended with the following plugins. Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |


### Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:
```sh
$ node app
```

Second Tab:
```sh
$ gulp watch
```

(optional) Third:
```sh
$ karma test
```
#### Building for source
For production release:
```sh
$ gulp build --prod
```
Generating pre-built zip archives for distribution:
```sh
$ gulp build dist --prod
```
### Docker
Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the Dockerfile if necessary. When ready, simply use the Dockerfile to build the image.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version} .
```
This will create the dillinger image and pull in the necessary dependencies. Be sure to swap out `${package.json.version}` with the actual version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on your host. In this example, we simply map port 8000 of the host to port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Verify the deployment by navigating to your server address in your preferred browser.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

See [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)


### Todos

 - Write MORE Tests
 - Add Night Mode

License
----

MIT


**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
