### `Spago` should work "out of the box"

```sh
spago init

# can be asked to install manually:
spago install form-urlencoded

spago repl
spago build
```


### Testing

```sh
npm install express
npm install xhr2

spago test
# or
spago test --main Test.Main
```
