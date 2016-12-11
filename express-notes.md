# Express Notes

# Contents
+ Extracting data from either URI or request body
  * req.params
  * req.query
  * req.body
+ App.params


# Extracting data from either URI or request body

## req.params

```js
router.get("/:urlTitle", (req, res, next) => {
    req.params.urlTitle
});
```
## req.query
Also is used when doing a form with method `GET`

```js
// /search?tag=foo
router.get("/search", (req, res, next) => {
    req.query.tag
});
```

## req.body
Used when doing a form with method `POST` and body-parser middleware

```js
router.post("/", (req, res, next) => {
    name: req.body.name,
    email: req.body.email
});
```

# Add.param
This allows you to process information in the parameters of the passed in URI.

For more information look at this [blog post](https://www.safaribooksonline.com/blog/2014/03/13/parameterized-routes-express-js/).

```js
// App.param - /:id
router.param("id", (req, res, next, id) => {
    Article.findById(id)
    .then((article) => {
        req._articleById = article; // Store the found article on the request object, that can be used in subsequent routes
        next(); // This is crucial to letting the program continue and not hang
    })
    .catch();
});
```
