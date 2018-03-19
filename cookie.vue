<template>
<div>
<div id ="vue_cookie_privacy" v-bind:style="{backgroundColor:backcolor}" v-if="cookie != true" v-cloak>
     <span v-bind:style="{ color: textcolor, fontSize: textsize }">
        {{text}}
        <button class="cookiebutton" v-on:click="accept_cookie">{{button}}</button>
     </span>
   </div>
</div>
</template>

<script>
export default {
    name: 'VueCookie',
    props: ['cookietext','cookiebutton','cookietextcolor','cookietextsize','cookiebackgroundcolor'],
    data: function() {
        return {
             text: this.cookietext,
             button: this.cookiebutton,
             textcolor: this.cookietextcolor,
             textsize: this.cookietextsize,
             backcolor: this.cookiebackgroundcolor
        }
    },
    method: {
      accept_cookie: function (){
        alert('Accept Cookie')
      }
    }
}
</script>

<style scoped>
[v-cloak] {
  display: none;
}

.c{
  color:green;
}

.a{
  color: violet;
}

.b{
  color: red
}

#vue_cookie_privacy {
  position: fixed;
  bottom: 0;
  width: 100%;
  text-align: center;
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
  line-height: 1.42857143;

}

.cookiebutton {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 25px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  border-radius: 5px 5px 5px 5px;
  cursor: pointer;
}
</style>
