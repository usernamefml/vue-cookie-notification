<template>
<div>
<div id ="vue_cookie_privacy" v-if="cookie != true" v-cloak>
     <span v-bind:class="{ 'a': isA, 'b': isB,'c': isC,'d': isD,'e': isE,'f': isF }">
        In order to give you the best experience, our website uses cookies. By continuing to use this site, you agree to our use of cookies.
        <button class="cookiebutton" v-on:click="accept_cookie">Accept</button>
     </span>
   </div>
</div>
</template>

<script>
export default {
    name: 'VueCookie',
    props: ['cookie-settings'],
    data: function() {
        return {
            data: "star rating",
             isA: true,
             isB: false,
             isC: false,
             isD: false,
             isE: false,
             isF: false,
             cookie: false
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
  background-color: violet;
}

.b{
  background-color: red
}

#vue_cookie_privacy {
  position: fixed;
  bottom: 0;
  width: 100%;
  background-color: #e8e8e8;
  color: #333333;
  font-size: 14px;
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
