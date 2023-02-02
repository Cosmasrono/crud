 <template>
   <main class="">
    <div class=" text-slate-900">
        Welcome to the CRUD

    </div>
    <form @submit.prevent="addItems" class=" flex flex-col justify-center items-center">
   <input type="text"  placeholder="enter new items">
   <button class="p-5 mt-10 bg-green-400 rounded-lg">Add something new</button>
    </form>
   <div class="">
   <ul>
    <li v-for="(item, index) in items" :key="index">
      {{ item }}
      <button @click="updateItem(index)" class=" items-center justify-start p-5 ">Edit</button>
      <button @click="deleteItem(index)" class=" items-center justify-start">Delete</button>
     
    </li>
  </ul>
</div>
   </main>
 </template>
 
 <script>
 export default {
    data(){
        return{
            items:[],
            newItems:'',
        }
    },
    methods:{
        addItems(){
            this.items.push(this.newItem)
            this.newItems='',
            localStorage.setItem('items', JSON.stringify(this.items));
        },
        updateItem(index){
            this.items[index] = prompt('Update item:', this.items[index])
        },
        deleteItems(index){
            this.items.slice(index,1)
            console.log(index);
        }
    },
    mounted(){
        const storedTodos= localStorage.getItem('items');
    if (storedTodos) {
      this.items = JSON.parse(storedTodos);
    }
 
 }
}
 </script>
 
 