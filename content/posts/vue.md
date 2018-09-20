+++
draft = false
date = 2018-09-11T00:55:08+08:00
title = "Vue"
slug = ""
tags = []
categories = []
+++


### 数据绑定、计算属性

<pre><ch>
<div id="post_display">
  <div class="img_line" v-for="postRow in postRows">
    <div class="img_frame" v-bind:style="frameStyle" v-for="post in postRow">
      <img v-bind:src="post.sample_url">
    </div>
  </div>
</div>
</ch></pre>

v-bind:style 数据绑定为计算属性时，计算属性函数的返回值为Object，采用Object的 key value 表示 style。而不能返回style 字符串。

<pre><c>
var vm = new Vue({
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


### 方法
<pre><ch class="html">
<div class="img_frame" v-bind:style="frameStyle" v-for="post in postRow">
  <img class="post_img" v-bind:src="post.preview_url" 

  onerror="javascript:reload(this)" 

  v-on:click="viewBigImage(post)">
</div>
</ch></pre>


<pre><c>
const vm = new Vue({
  el: "#post_display",
  data: {
    curPost: {
      file_url: "",
      id: -1,
      author: "null",
      tags: ""
    },
  },
  methods: {
    viewBigImage: function (post) {
      if (post) {
        document.getElementById('big_image_background').style.backgroundImage = `url(${post.preview_url})`;
        document.getElementById('big_image').src = post.file_url;
        document.getElementById('big_view').hidden = false;
        this.curPost = post;
        document.body.style.overflowY = "hidden";

      }
      else {
        document.body.style.overflowY = "unset";
        document.getElementById('big_view').hidden = true;
      }
      console.log(post);
    }
  }
}
</c></pre>

### 使用 DOM API 而不使用数据绑定的情况

- 页面需要立即更新
- 操作不复杂
