# Sass Example

## Getting Started
`npm install -g sass`

* Create a directory called `scss`
* Create an index file in that directory `scss/index.scss`
* Open terminal/gitbash

## Running Sass preprocessor

`sass --watch scss/index.scss public/css/styles.css`

This does the following
Argument | What it does
---------|-------------
`sass`   | The global CLI command
`--watch`| Like nodemon, will re-run after any changes (this is optional)
`scss/index.scss` | The path to your main `index.scss` file
`public/css/styles.css` | The output path and filename (destination)

## Note
* All your current css can be pasted into a `.scss` file and it will still work the same
* Anthing in your destination file (ex `public/css/styles.css`) will be overwritten

## Features
[https://sass-lang.com/guide#topic-4](https://sass-lang.com/guide#topic-4)

### **Variables**
```scss
$primary-color: #333;
button {
    color: $primary-color;
}
```

### **Nesting**
```scss
ul {
    padding: 10px 5px;
    li {
        margin: 0;
        &.text-blue {
            color: cornflowerblue;
        }
        .text-italic {
            font-style: italic;
        }
    }
}
```
Turns into:
```scss
ul { padding: 10px 5px; }
ul li {
    margin: 0;
}
ul li.text-blue {
    color: cornflowerblue;
}
ul li .text-italic {
    font-style: italic;
}
```


### **Partials**
* You can make many .scss files (partials) and it bundles them togther in one .css file
* Name files with an underscore `_header.scss`, `_about.scss`
* in your `index.scss` file you use these partials with no underscore; `@use 'header';` and `@use 'about';` this will include them in your final styles.css file in the order they are written

### **Extending Styles**
```scss
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}


.message {
  // This extends all the above styles
  @extend %message-shared;
  // Can always add more
  background-color: cornflowerblue;
}
```

### Operators
You can even do math and let Sass figure it out
```scss
.main-column{
  float: left;
  width: 600px / 960px * 100%;
}
```
Output
```scss
.main-column {
  float: left;
  width: 62.5%;
}
```
