<template>
  <p :class="{active:isActive}">{{state.count}}</p>

  <p>Veux-tu incrementer la valeur <span class="color-red">{{ publishedBooksMessage}}</span></p>

  <h1 v-if="isActive">le contenu</h1>
  <h2 v-else>je suis le else</h2>
  <ul>
    <li v-for="(item,index) in items" :key="index">
     {{item.message}}
    </li>
  </ul>
  <p>{{message}}</p>
  <input v-model="message" placeholder="votre message">

  <button @click.prevent="increment" class="btn btn-primary color">Incrémenter</button>
  <button @click="greet" class="btn btn-secondary" @keyup.delete="delect" v-if="isDelect" >Greet</button>
</template>

<script setup>
import { reactive,nextTick, computed,ref } from 'vue'

const name = ref('Vue.js')
const message = ref('')
 const isDelect= ref(false);


function greet(event) {
  alert(`Hello ${name.value}!`)
  // `event` is the native DOM event
  if (event) {
    alert(event.target.tagName)
  }
}
function delect(){
  return !isDelect.value;

}

    const author = reactive({
      name: 'John Doe',
      books: [
        'Vue 2 - Advanced Guide',
        'Vue 3 - Basic Guide',
        'Vue 4 - The Mystery'
      ]
    })
  const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
  const isActive=ref(true);

    const state = reactive({ count: 0 })
    function increment() {
      state.count++
      nextTick(() => {
        // access updated DOM
      })
    }
    const publishedBooksMessage = computed(() => {
      return author.books.length > 0 ? 'Yes' : 'No'
    })

const color =computed(()=>state.count>5?"red":"green")






</script>

<style scoped>
  .color{
    background-color: v-bind(color);
  }
  .active{
    font-weight: 700;
    color: red;
  }
</style>