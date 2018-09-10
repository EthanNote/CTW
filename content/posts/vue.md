+++
draft = false
date = 2018-09-11T00:55:08+08:00
title = "Vue"
slug = ""
tags = []
categories = []
+++


### 数据绑定、计算属性

```
<div id="post_display">
  <div class="img_line" v-for="postRow in postRows">
    <div class="img_frame" v-bind:style="frameStyle" v-for="post in postRow">
      <img v-bind:src="post.sample_url">
    </div>
  </div>
</div>
```

v-bind:style 数据绑定为计算属性时，计算属性函数的返回值为Object，采用Object的 key value 表示 style。而不能返回style 字符串。

<pre><c>var vm = new Vue({
      el: "#post_display",
      data: {
        posts: [],
        rows: 4,
      },
      computed: {
        postRows: function () {
          var result = [];
          var i = 0;
          while (1) {
            var nextLine = this.posts.slice(this.rows * i, this.rows * (i + 1));
            if (nextLine.length <= 0) {
              break;
            }
            result.push(nextLine);
            i++;
          }
          return result;
        },

        frameStyle: function () {
          return { width: `${100 / this.rows}%` }
        }

      }
    })
</c></pre>