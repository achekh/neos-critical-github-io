---
title: "Form"
slug: "form"
excerpt: "Component that holds form elements and submits their data."
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Apr 10 2023 05:14:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jun 15 2023 11:17:37 GMT+0000 (Coordinated Universal Time)"
layout: "default"
parent: "Form components"
grand_parent: "Components"
---
# Form 
*** 
Form. It submits its [switch](doc:switch), [input](doc:input), [checkbox](doc:checkbox), [slider](doc:slider), [radio](doc:radio), and [picker](doc:picker) information input by the user.

When the user clicks the [button](doc:button) component whose `form-type` is `submit` , the values in the form component will be submitted, and a name needs to be added as the key in the form component.

| Attribute  | Type          | Required | Description                                                                                                                        |
| :--------- | :------------ | :------- | :--------------------------------------------------------------------------------------------------------------------------------- |
| bindsubmit | Event Handler | No       | The `submit` event triggered for the data carried by the form component: `event.detail = {value : {'name': 'value'} , formId: ''}` |
| bindreset  | Event Handler | No       | The `reset` event triggered when the form is reset.                                                                                |

### Sample code

```javascript
// javascript
Page({
  formSubmit(e) {
  	console.log('A submit event occurred in `form`, which carried the data', e.detail.value)
  },
  formReset() {
  	console.log('A `reset` event occurred in `form`')
  }
})
```
```xml
<!--WXML-->
{% raw %}
<form bindsubmit="formSubmit" bindreset="formReset">
  <view class="section section_gap">
    <view class="section__title">switch</view>
    <switch name="switch" />
  </view>
  <view class="section section_gap">
    <view class="section__title">slider</view>
    <slider name="slider" show-value></slider>
  </view>
  <view class="section">
    <view class="section__title">input</view>
    <input name="input" placeholder="please input here" />
  </view>
  <view class="section section_gap">
    <view class="section__title">radio</view>
    <radio-group name="radio-group">
      <label>
      	<radio value="radio1" />
      	radio1
      </label>
      <label>
      	<radio value="radio2" />
      	radio2
      </label>
    </radio-group>
  </view>
  <view class="section section_gap">
    <view class="section__title">checkbox</view>
    <checkbox-group name="checkbox">
      <label>
      	<checkbox value="checkbox1" />
      	checkbox1
      </label>
      <label>
      	<checkbox value="checkbox2" />
      	checkbox2
    </label>
    </checkbox-group>
  </view>
  <view class="btn-area">
    <button form-type="submit">Submit</button>
    <button form-type="reset">Reset</button>
  </view>
</form>

{% endraw %}
```

### Built-in component behaviors

Form components can automatically identify the following built-in behaviors:

- wx://form-field
- wx://form-field-group
- wx://form-field-button

### wx://form-field

It makes the custom components behave like form controls. The form components can identify these custom components and add a submit event to return the field name of the component and its corresponding field value. This will add the following two properties:

| Attribute | Type        | Describe                  |
| :-------- | :---------- | :------------------------ |
| name      | String      | Field names in the form.  |
| value     | Arbitrarily | Field values in the form. |

### Code example

```javascript
// JavaScript
// custom-form-field.js
Component({
 behaviors: ['wx://form-field'],
 data: {
   value: ''
 },
 methods: {
   onChange: function (e) {
     this.setData({
       value: and.detail.value,
     })
   }
 }
})
```

### wx://form-field-group

The send form component recognizes all form controls within this custom component. For example, the page is structured as follows:

```xml
<!--WXML-->
{% raw %}
<form bindsubmit="submit">
  <custom-comp></custom-comp>
  <button form-type="submit">submit</button>
</form>
{% endraw %}
```

The structure of the assembly `custom-component`  is as follows:

```xml
<!--WXML-->
{% raw %}
<input name="name" />
<switch name="student" />
{% endraw %}
```

If the component `custom-component` is configured with:

```javascript
// JavaScript
Component({
 behaviors: ['wx://form-field-group']
})
```

At this point, the form's `submit` event `value` will include `name` and `student` .

### wx://form-field-button

The send form component recognizes the button. If the custom component has settings inside the form-type of button, it will be checked by the accept form. For example, the page is structured as follows:

```xml
<!--WXML-->
{% raw %}
<form bindsubmit="submit">
  <input name="name" Placeholder = "Please enter name"></input>
  <custom-comp></custom-comp>
</form>
{% endraw %}
```

The structure of the assembly `custom-component`  is as follows:

```xml
<!--WXML-->
{% raw %}
<button form-type="submit">submit</button>
{% endraw %}
```

If the component `custom-component` is configured with:

```javascript
// JavaScript
Component({
 behaviors: ['wx://form-field-button']
})
```

At this point, clicking the button will trigger form's submit event.
