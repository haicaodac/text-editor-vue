# Gem Text Editor

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

A vue package makes it easy to create and edit the best editor.

## Installation

You can install the npm package in save mode to save it into dependencies

```shell
npm install --save gem-text-editor
```

## Getting Started

You can start with a basic template
```html
<template>
  <GemTextEditor ref="editor" v-model="content" />
  <button @click="getContent()">Get content</button>
</template>

<script>
  import GemTextEditor from "gem-text-editor";
  components: {
    GemTextEditor
  },
  data() {
    return {
      content: ""
    }
  },
  methods: {
    getContent() {
      console.log("Content: ", this.content);
    }
  }
</script>
```

### Init Settings

You need to add an **init** attribute that includes the definition
```html
<template>
  <GemTextEditor ref="editor" :init="initSettings" />
</template>

<script>
  import GemTextEditor from "gem-text-editor";
  components: {
    GemTextEditor
  },
  data() {
    return {
      initSettings: {
        options: [
          "bold",
          "italic",
          "underline"
        ]
      }
    };
  },
</script>
```

#### options
You can change the position of the options to change the display
```html
"bold",
"italic",
"underline",
"justifyLeft",
"justifyCenter",
"justifyRight",
"orderedList",
"unorderedList",
"color",
"link",
"image"
```
#### minHeight
```html
200px
```
#### maxHeight
```html
200px
```
**unset** (If not to maxHeight, the height will automatically increase)

#### stickyTool
If you use maxHeight as unset then you may need to consider this attribute
```html
false
```
### Listen
The functions will be generated by the editor to serve different purposes
#### uploadImages
Listening to this function helps you upload files to the server. This function only happens when your options contain "image".
```html
<template>
    <GemTextEditor ref="editor" @uploadImages="uploadImages" />
</template>
<script>
  methods: {
    uploadImages(images) {
      setTimeout(() => {
        let url =
          "https://image.shutterstock.com/image-photo/bright-spring-view-cameo-island-260nw-1048185397.jpg";
        this.$refs.editor.insertImage({
          src: url,
          alt: "alt",
          title: "title"
        });
      }, 2000);
    },
  }
</script>
```
#### onChange
Any change in content in the editor, you can listen to the changes
```html
<template>
    <GemTextEditor ref="editor" @onChange="onChange" />
</template>
<script>
  methods: {
    onChange(content) {
      console.log("Content: ", content)
    },
  }
</script>
```
### Trigger
You can trigger the editor to know your desired actions to interact with the editor
#### insertImage
Add an image inside the editor's content
```html
.insertImage({
  src: "image.png",
  alt: "alt",
  title: "title"
});
```
#### getContent
Get the content data currently in the editor. Data returned as string
Add an image inside the editor's content
```html
.getContent();
```




## Questions
If you have any questions, please contact via email: haicaodac@gmail.com
