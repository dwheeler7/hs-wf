# Embedding & styling HubSpot forms in Webflow
HubSpot forms are ugly. Webflow forms don't really work with HubSpot. Here's your fix: embed HubSpot forms and style them from Webflow.

## 1. Create form in HubSpot
- Select `Set as raw HTML form`
- Copy the form embed code

## 2. Edit HubSpot's form embed code

**HubSpot will provide the following HTML code snippet:**

```html
<script charset="utf-8" type="text/javascript" src="//js.hsforms.net/forms/embed/v2.js"></script>
<script>
  hbspt.forms.create({
    portalId: "{portal id}",
    formId: "{form id}",
    region: "na1"
  });
</script>
```

**Add these two lines:**

```html
<script charset="utf-8" type="text/javascript" src="//js.hsforms.net/forms/embed/v2.js"></script>
<script>
  hbspt.forms.create({
    portalId: "{portal id}",
    formId: "{form id}",
    region: "na1",
    css: "",
    cssClass: "hbspt-form" 
  });
</script>
```

## 3. Style the form in Webflow
Now we'll drop CSS - that styles the embedded HubSpot forms - into Webflow.

**Here's some CSS using [the Untitled UI style]([url](https://www.untitledui.com/)). Update it with your's:**

```html
<style>
.hbspt-form form {
  display: flex;
  flex-direction: column;
  grid-gap: 1rem;
}
.hbspt-form input, .hbspt-form select {
    color: #8f9295;
    background-color: #fff;
    border: 1px solid #d0d5dd;
    border-radius: .5rem;
    width: 100% !important;
    height: auto;
    min-height: 2.75rem;
    margin-bottom: 0;
    padding: .5rem .875rem;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Noto Sans, Ubuntu, Cantarell, Helvetica Neue, Oxygen, Fira Sans, Droid Sans, sans-serif;
    font-size: 1rem;
    line-height: 1.5;
    transition: all .3s;
    display: inline-block;
    box-shadow: 0 1px 2px rgba(16, 24, 40, .05);
}
.hbspt-form input:focus {
  color: #101828;
   border-color: #bbcefb;
   box-shadow: 0 1px 2px rgba(16, 24, 40, .05), 0 0 0 4px #ebf6ff;
}
.hbspt-form input[type=submit] {
  color: #fff;
  text-align: center;
  white-space: nowrap;
  background-color: #4a4ea3;
  border: 1px solid #4a4ea3;
  border-radius: .5rem;
  justify-content: center;
  align-items: center;
  padding: .625rem 1.125rem;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Noto Sans, Ubuntu, Cantarell, Helvetica Neue, Oxygen, Fira Sans, Droid Sans, sans-serif;
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.5;
  text-decoration: none;
  transition: all .3s;
  display: flex;
  box-shadow: 0 1px 2px rgba(16, 24, 40, .05);
}
.hbspt-form .input {
  margin-right: 0px !important;
}
.hbspt-form input[type=submit]:hover {
  cursor: pointer;
}
.hbspt-form label {
  color: #344054;
  margin-bottom: .5rem;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Noto Sans, Ubuntu, Cantarell, Helvetica Neue, Oxygen, Fira Sans, Droid Sans, sans-serif;
  font-size: .875rem;
  font-weight: 500;
  line-height: 1.5;
}
.hs-form fieldset {
  display: none;
}
.hs-form .form-columns-2 {
  display: flex !important;
  grid-gap: 1rem;
}
.hs-form fieldset:nth-child(-n+4) {
  display: block;
  max-width: 100%;
}
.hs-form  legend {
  color: #475467;
  letter-spacing: normal;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Noto Sans, Ubuntu, Cantarell, Helvetica Neue, Oxygen, Fira Sans, Droid Sans, sans-serif;
  font-size: .875rem;
  line-height: 1.5;
	margin-bottom: 1rem;
}
</style>
```

## 4. Drop this CSS into Webflow everywhere
- Navigate to your Webflow site settings, then _Custom code_
- Paste your CSS in the _Head code_ and republish your site.

## 4. Create forms in Webflow
Now, just drop the form embed code into an _HTML Embed_ Webflow element. Note: the form will span 100% the width of the _HTML Embed_ element.
