<template>
  <div class="hello container">
    <h1>{{ msg }}</h1>

        <ButtonElement/>

  </div>
</template>

<script>
import ButtonElement from "@/components/ButtonElement";
export default {
  name: 'HelloWorld',
  props: {
    msg: String,

  },
  components: {
    ButtonElement
  },
  data() {
    return {
      objectOfAttrs: {
        id: 'container',
        class: 'wrapper'
      },
      value:""
    }
  },

  methods:{
    foo:function (){
        alert('hello')
    },
    rawHtml:function () {
      return "je suis du html brute"
    },
    condition:function () {
        return true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
