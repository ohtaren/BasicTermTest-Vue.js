<template>
  <div id="app">
    <div class="top">
      <div class="content">
        <div class="title">
          <p>Todo List</p>
        </div>
        <div class="add">
          <input type="text" v-model="name" class="input-add"/>
          <button @click="doadd" class="button-add">追加</button>
        </div>
        <div class="update">
          <ul>
            <li v-for="(item,index) in list" :key="index">
              <input type="text" class="input-update"/>
              <div>
                <button @click="doupdate" class="button-update">更新</button>
                <button @click="dodelete" class="button-delete">削除</button>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default{
  data() {
    return{
      name:"",
      list: [
        {name:"todo"}
      ]
    };
  },

  methods: {
    doadd(){
      this.list.push({
        name:this.name
      });
    },

    doupdate(){
      this.list[0] = "name"
    },

    dodelete(){
      this.list.splice(0,1);
    }

  }
};


</script>


<style>
html, body, div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
abbr, address, cite, code,
del, dfn, em, img, ins, kbd, q, samp,
small, strong, sub, sup, var,
b, i,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, figcaption, figure,
footer, header, hgroup, menu, nav, section, summary,
time, mark, audio, video {
    margin:0;
    padding:0;
    border:0;
    outline:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

body {
    line-height:1;
}

article,aside,details,figcaption,figure,
footer,header,hgroup,menu,nav,section {
    display:block;
}

nav ul {
    list-style:none;
}

blockquote, q {
    quotes:none;
}

blockquote:before, blockquote:after,
q:before, q:after {
    content:'';
    content:none;
}

a {
    margin:0;
    padding:0;
    font-size:100%;
    vertical-align:baseline;
    background:transparent;
}

/* change colours to suit your needs */
ins {
    background-color:#ff9;
    color:#000;
    text-decoration:none;
}

/* change colours to suit your needs */
mark {
    background-color:#ff9;
    color:#000;
    font-style:italic;
    font-weight:bold;
}

del {
    text-decoration: line-through;
}

abbr[title], dfn[title] {
    border-bottom:1px dotted;
    cursor:help;
}

table {
    border-collapse:collapse;
    border-spacing:0;
}

/* change border colour to suit your needs */
hr {
    display:block;
    height:1px;
    border:0;  
    border-top:1px solid #cccccc;
    margin:1em 0;
    padding:0;
}

input, select {
    vertical-align:middle;
}

html {
  background-color: #15202b;
}
* {
  color: white;
  font-family: "Noto Sans JP";
}

/* ////////////////////////////////////////////////////////////////// */

.top{
  background-color: darkslateblue;
  height: 100vh;
  width: 100vw;
  position: relative;
}

.content{
  background-color: #fff;
  width: 50vw;
  padding: 30px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 10px;
}

.title{
  font-weight: bold;
  font-size: 24px;
  margin-bottom: 15px;
}

.title p{
  color: #000;
}

.add{
  margin-bottom: 15px;
  justify-content: space-between;
  display: flex;
}

.input-add{
  width: 80%;
  padding: 5px;
  border-radius: 5px;
  border: 1px solid #ccc;
  appearance: none;
  color: #000;
  font-size: 14px;
  outline: none;
}

.button-add{
  text-align: left;
  border: 2px solid #dc70fa;
  font-size: 12px;
  color: #dc70fa;
  background-color: #fff;
  font-weight: bold;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.4s;
  outline: none;
}

.update{
  margin-bottom: 5px;
  justify-content: space-between;
  display: flex;
}

.input-update{
  width: 30%;
  padding: 5px;
  border-radius: 5px;
  border: 1px solid #ccc;
  appearance: none;
  color: #000;
  font-size: 14px;
  outline: none;
}

.button-update{
  text-align: left;
  border: 2px solid #fa9770;
  font-size: 12px;
  color: #fa9770;
  background-color: #fff;
  font-weight: bold;
  padding: 8px 16px;
  margin-right: 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.4s;
  outline: none;
}

.button-delete{
  text-align: left;
  border: 2px solid #71fadc;
  font-size: 12px;
  color: #71fadc;
  background-color: #fff;
  font-weight: bold;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: 0.4s;
  outline: none;
}

</style>