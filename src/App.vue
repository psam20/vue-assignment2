<template>
  <div id="app">
    <h1>
      Demonstration of passing Data Between Components,styles Demo
    </h1>
    <h4 v-if="recent">
      Recently Added Book :- {{Recently.title.toUpperCase()}},{{Recently.publication}},${{Recently.price}}
      
    </h4>
    <hr/>
    <Book
   
     :books="Books"
     @add-book="addBooks"
     />
  </div>
</template>
<script>
import Book from './components/BookComponent.vue'

export default {
  name: 'App',
  components: {
    Book
  },
  data(){
    return {
      Books :[
        {
          title:'MongoDb in Action',
          publication:'2011',
          price:'38'
        },
         {
          title:'Javascript: The Good Parts',
          publication:'2008',
          price:'21'
        }
      ],
      Recently:{},
      recent:false
    }
  },
  methods:{
    addBooks(data){

      console.log(data)
      this.Recently=data
      this.recent=true
      this.Books.push(data)

    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  color:brown;
}
h4{
   color:rgba(233,110,130,0.8)
}
</style>
