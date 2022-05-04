<template>
    <div class>
        <div v-for="post in a[0]" v-bind:key="post.id" class="list-group-item list-group-item-action shadow files" style="width:50%" >
            {{post}}
        </div>
        <div v-for="post in a[1]" v-bind:key="post.id" class="list-group-item list-group-item-action shadow files" style="width:50%" >
            {{post}}
        </div>
        
    </div>
</template>

<script>
const fs = require("fs");
const { resolve } = require("path");

const fn = (path) => {
    const contents = fs.readdirSync(path);

    const files = [];
    const folders = [];

    contents.forEach(el => {
        var localpath = resolve(path, el);
        var lstat = fs.lstatSync(localpath,);
        if(lstat.isFile()) files.push(el);
        if(lstat.isDirectory()) folders.push(el);
    });

    return [folders,files];
}
export default {
    
      data(){
            var a=fn('D:/Games')
        return{
            a
        }
  },
  name: 'App',
  components: {
  }

}
</script>

<style>
.file_field_btn
{
    width: 100%;
    background-color: rgba(255, 255, 255, 0);
    border-block-color: rgba(255, 255, 255, 0);
    border-color: rgba(255, 255, 255, 0);
}
.files
{
    text-align: left;
    user-select: none;
    font-family: Arial, Helvetica, sans-serif;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
::-webkit-scrollbar {
    width: 10px;
}

::-webkit-scrollbar-track {
    -webkit-box-shadow: inset 0 0 100px rgba(73, 66, 66, 0.301); 
    border-radius: 1px;
}

::-webkit-scrollbar-thumb {
    border-radius: 1px;
    width: 6px;
    -webkit-box-shadow: inset 0 0 100px rgb(0, 0, 0); 
}
</style>
