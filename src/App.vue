<template>
  <div id="app">
    <div class="top">
      <div class="content">
        <div class="title">
          <p>Todo List</p>
        </div>
        <div class="add">
          <input type="text" v-model="newTodo" class="input-add"/>
          <button class="button-add" @click="doadd">追加</button>
        </div>
        <div class="update"  v-for="item in todos" :key="item.id">
              <input type="text" v-model="item.name" class="input-update"/>
              <div>
                <button @click="doupdate(item.id,item.name)" class="button-update">更新</button>
                <button @click="dodelete(item.id)" class="button-delete">削除</button>
              </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default{
  data() {
    return{
     todos:[
    
     ],

       newTodo:""
    };
  },

  methods: {
    async doadd(){
      console.log(this.newTodo);
      const sendData = {
        name: this.newTodo,
      };
      await axios.post("https://pacific-oasis-86450.herokuapp.com/api/item",sendData);
      this.getTodos();
      this.newTodo = "";
      
      
    },

    async doupdate(id,name){
      const sendData = {
        name:name,
      };
      await axios.put("https://pacific-oasis-86450.herokuapp.com/item/" + id, sendData);
      this.getTodos();
    },

    async dodelete(id){
      await axios.delete("https://pacific-oasis-86450.herokuapp.com/api/item/" + id);
      this.getTodos();
    },

    async getTodos(){
      console.log("データを取得しました");
      const response = await axios.get("https://pacific-oasis-86450.herokuapp.com/api/item");
      this.todos = response.data.data;
    },
  },

  mounted(){
    this.getTodos();
  },
}


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