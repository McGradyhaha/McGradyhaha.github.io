---
layout: post
author: WhyK
comments: true
date: 2018-07-26 9:05:32+10:00
tags: [node.js]
title: Understanding module.exports and exports in Node.js
---

#### What is a Module

A module brings related functions into a unit of code. Let's imagine the we want to create a file named `Hello.js`and it contains the following two functions:

```node.js
// Hello.js
function helloEnglish(){
    var hello = 'Hello';
    console.log(hello);
}

function helloSpanish(){
    var hello = 'Hola';
    console.log(hello);
}

function helloChinese(){
    var hello = '你好';
    console.log(hello);
}
```

#### Exporting a Module

Imagine the file can be utilized in other files. we need `module.exports` to accomplish that.

```node.js
// Hello.js
module.exports = {
    function helloEnglish(){
        var hello = 'Hello';
        console.log(hello);
    }

    function helloSpanish(){
        var hello = 'Hola';
        console.log(hello);
    }

    function helloChinese(){
        var hello = '你好';
        console.log(hello);
    }
};
```

#### Importing a Module

Let import `Hello.js` to a new file named `main.js`. The keyword `require` is used in Node.js to import modules, and whole structure shows as follows

```node.js
var hello = require("./Hello.js")

hello.helloEnglish();
hello.helloChinese();
```

