* .babelrc 에서 modules 'false'로 되어 있을 시, ES6 모듈 사용할 수 없음
~~~
{
  "presets": [
    ["env", {
      "modules": false,
      "targets": {
        "browsers": ["> 1%", "last 2 versions", "not ie <= 8"]
      }
    }],
    "stage-2"
  ],
  "plugins": ["transform-vue-jsx", "transform-runtime"]
}
~~~

* module 문법 사용하고 싶을 경우, `modules` 옵션을 `true`로 하거나 `"modules": false,` 를 삭제한다

* reference : https://babeljs.io/docs/plugins/preset-es2015/
~~~
modules
"amd" | "umd" | "systemjs" | "commonjs" | false, defaults to "commonjs".

Enable transformation of ES6 module syntax to another module type.

Setting this to false will not transform modules.
~~~
