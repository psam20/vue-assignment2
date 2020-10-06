<template>
  <div>
    <h1 class="bookHeader">Book List Technology</h1>
  </div>
   <div class="bookList"> 
       <table align="center">
         <tr>
           <th>
             Title
           </th>
           <th>Publication Year</th>
           <th>Price</th>
         </tr>
         <tr v-for="book in books">
           <td>{{book.title.toUpperCase()}} </td>
           <td>{{book.publication}}</td>
           <td>${{book.price}}</td>
         </tr>
       </table>
   </div>
   <div class="addBookList">
     Enter Book Title:- <input type="text" v-model="bookTitle" />
     Enter Publication Year <input type="text" v-model="publicationYear" />
     Enter Price <input type="string" v-model="price"  />
   </div>
   <div class="addBook">
     <button @click="addBook">
       Add Book
     </button>
   </div>
  
</template>

<script>
export default {
  name: 'Book',
  props: [
    'books'
  ],
  emits:['add-book'],
  data(){
    return{
      bookTitle :'',
      publicationYear:'',
      price:''

    }
  },
  methods:{
    addBook(){
      if(this.bookTitle == '' || this.publicationYear=='' || this.price ==''){
        console.log("obj is empty")
        return
      }
      // console.log("this is bookTitle",this.bookTitle)
      this.$emit('add-book',{
        title:this.bookTitle,
        publication:this.publicationYear,
        price:this.price
      })
      this.bookTitle='';
      this.publicationYear='';
      this.price='';

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.bookHeader{
  color:blue;
}
table,th,td {
  border : 1px solid black;
  color:rgba(233,132,34,0.8)
}
td{
  color:rgba(233,110,120,0.6)
}
.bookList, .addBookList {
  margin-bottom :20px;
}
</style>
