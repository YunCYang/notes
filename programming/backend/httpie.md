# HTTPie

## Purpose
Command line HTTP client for easy backend testing.

## Example Requests

```
$ http -v POST :3000/api/grades/3 name="John" course="httpie" grade=80
```

-          http: for HTTPie commands
-            -v: shorthand for --verbose. Print the whole HTTP exchange including
                 request and response.
-          POST: method type. Common methods are GET, POST, PUT, DELETE, PATCH.
-         :3000: shorthand for http://localhost:3000 .
- /api/grades/3: use this address to check if the request is recognized in the
                 code.
-   name="John": contents in the body of the request. Optional. Use req.body to
                 find the input body.

## Resource
- [Official Documentation](https://httpie.org/doc)


[Back](../../README.md)
