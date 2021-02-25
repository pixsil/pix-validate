# Vue Validation component

You can use this package to add easy validation to your Laravel Vue project. This package makes it easy to add field translations as attribute instead of writing long 'Custom Validation Attributes' translations inside your lang file.

## Features

* Very small and easy to use
* Validation with a single line
* Works seamlessly with the Pixsil VueFrom package
* Easy to add alternative field names for if you use a different language
* Possible to override a validation message by attribute
* Uses Bootstrap style classes if needed

## Requirements

This package uses Pixsil VueFrom package to receive the errors:

https://github.com/pixsil/vueform

## Donate

Find this project useful? You can support me on Patreon

https://www.patreon.com/pixsil

## Installation

Add this to your app.js
```javascript
// import
import PixValidate from "./tools/pix-validate/pix-validate";

// use in vue
Vue.use(PixValidate);
```

## Usage

Add 

```vue
<pix-validate :vue-form="vueForm" field="fieldname"></pix-validate>
```

## Full example

Check out the example folder for a full example of a Vue component with pix-validation inside it.