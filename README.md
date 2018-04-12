# JSON-Vuer
A vue-component that renders JSON-data to fully customizable readable table-form.

## What is json-vuer?
JSON-Vuer (JSON-Viewer) is a component for vue.js. You can pass a valid JSON-string as a prop and render it as collapsible and expandable HTML.
Thus far JSON-Vuer will render nested JSON-data up to seven levels deep.

## Why would I need this?
You might either want to use this component for yourself for debugging purposes.
You also might want to display hierarchic data structures in a more presentable form to the user. You then can customize the HTML of the vue-template or its CSS (BEM-CSS).

## How to get started
* (Pull in vue.js and create a vue-object)
* Transpile the JsonVuer.vue with laravel-mix or vue-cli.
* Register JSON-Vuer as a component. (Import either transpiled component or vue-file before transpiling your JS)
* Embed your component and pass your JSON-String as a prop:
    ```<json-vuer :json=MyJSONString ></json-vuer>```
* Experiment!

## May I contribute?
Please!
