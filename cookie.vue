<template>
<div>
<div id ="vue_cookie_privacy" v-bind:style="{backgroundColor:backcolor}" v-if="nocookie" v-cloak>
     <span v-bind:style="{ color: textcolor, fontSize: textsize }">
        {{text}}
        <button class="cookiebutton" v-on:click="accept_cookie()">{{button}}</button>
     </span>
   </div>
</div>
</template>

<script>
export default {
  name: "VueCookie",
  props: [
    "cookietext",
    "cookiebutton",
    "cookietextcolor",
    "cookietextsize",
    "cookiebackgroundcolor",
    "cookiename",
    "cookievalue",
    "cookieexdays"
  ],
  data: function() {
    return {
      nocookie: true,
      text: this.cookietext,
      button: this.cookiebutton,
      textcolor: this.cookietextcolor,
      textsize: this.cookietextsize,
      backcolor: this.cookiebackgroundcolor,
      cname: this.cookiename,
      cvalue: this.cookievalue,
      exdays: this.cookieexdays
    };
  },
  methods: {
    accept_cookie: function() {
      this.setCookie(this.cname, this.cvalue, this.exdays);
    },
    setCookie: function(cname, cvalue, exdays) {
      var d = new Date();
      d.setTime(d.getTime() + exdays * 24 * 60 * 60 * 1000);
      var expires = "expires=" + d.toUTCString();
      document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
      this.nocookie = false;
    },
    getCookie: function(cname) {
      var name = cname + "=";
      var decodedCookie = decodeURIComponent(document.cookie);
      var ca = decodedCookie.split(";");
      for (var i = 0; i < ca.length; i++) {
        var c = ca[i];
        while (c.charAt(0) == " ") {
          c = c.substring(1);
        }
        if (c.indexOf(name) == 0) {
          return c.substring(name.length, c.length);
        }
      }
      return "";
    }
  },
  mounted: function() {
    var self = this;
    var x = self.getCookie(this.cname);
    if(x != '' || undefined){
      console.log(x)
        this.nocookie = false;
    }
  }
};
</script>

<style scoped>
[v-cloak] {
  display: none;
}

.c {
  color: green;
}

.a {
  color: violet;
}

.b {
  color: red;
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
  background-color: #4caf50;
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
