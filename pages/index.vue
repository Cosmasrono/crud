<template>
  
  <div class=" flex flex-col">
          <nuxt-link to="" class=" flex flex-row justify-end bg-slate-900 text-white text-xl pr-3">Home</nuxt-link >
          <nuxt-link to="" class=" flex flex-row justify-end bg-slate-900 text-white text-xl pr-3">Login</nuxt-link >
    </div>
    <div class=" flex items-center justify-center bg-slate-600 flex-col p-2">
      <h1 class=" text-6xl text-white">NUXT CRUD <span class=" text-yellow-400">TRY ME</span></h1>
    <input type="text" placeholder=" enter your item" v-model="newItemText" class=" p-4 rounded-md mt-5" required/>
    <button @click="addItem" class=" bg-slate-900 text-white rounded-sm mt-5">Add Item</button>
    <div >
      <li v-for="item in items" :key="item.id" class=" gap-6 flex-row">
        {{ item.text }}
        <button @click="editItem(item)" class=" bg-slate-900 text-white mt-3 mr-6 border-white rounded-sm">edit</button>
        <button @click="deleteItem(item)" class=" bg-slate-900 text-white mt-3 border-white rounded-sm">Delete</button>
      </li>
    
  </div>
    <div v-if="editingItem" class=" gap-3 flex flex-row items-center justify-center">
      <input type="text" v-model="editingItem.text" />
      <button @click="saveItem" class="">Save</button>
      <button @click="cancelEdit">Cancel</button>
    </div>
  </div>
  <div class=" flex items-center justify-center">
<div class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
  <a href="#">
      <img class="rounded-t-lg" src="../assets/image.jpg" />
  </a>
  <div class="p-5">
      <a href="#">
          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Noteworthy technology acquisitions 2021</h5>
      </a>
      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.</p>
      <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
          Read more
          <svg aria-hidden="true" class="w-4 h-4 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
      </a>
  </div>
</div>
<!-- <div class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
  <a href="#">
      <img class="rounded-t-lg" src="/docs/images/blog/image-1.jpg" alt="" />
  </a>
  <div class="p-5">
      <a href="#">
          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Noteworthy technology acquisitions 2021</h5>
      </a>
      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.</p>
      <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
          Read more
          <svg aria-hidden="true" class="w-4 h-4 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
      </a>
  </div>
</div> -->
<!-- <div class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
  <a href="#">
      <img class="rounded-t-lg" src="/docs/images/blog/image-1.jpg" alt="" />
  </a>
  <div class="p-5">
      <a href="#">
          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">Noteworthy technology acquisitions 2021</h5>
      </a>
      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">Here are the biggest enterprise technology acquisitions of 2021 so far, in reverse chronological order.</p>
      <a href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
          Read more
          <svg aria-hidden="true" class="w-4 h-4 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
      </a>
  </div>
</div> -->

  </div>

<footer class="fixed bottom-0 left-0  w-full p-4 bg-slate-900 border-t border-gray-200 shadow md:flex md:items-center md:justify-between md:p-6 dark:bg-gray-800 dark:border-gray-600">
  <span class="text-sm text-white sm:text-center dark:text-gray-400">@cossi wing001@2023. All Rights Reserved.
  </span>
  <ul class="flex flex-wrap items-center mt-3 text-sm text-white dark:text-gray-400 sm:mt-0">
      <li>
          <a href="#" class="mr-4 hover:underline md:mr-6 ">About</a>
      </li>
      <li>
          <a href="#" class="mr-4 hover:underline md:mr-6">Privacy Policy</a>
      </li>
      <li>
          <a href="#" class="mr-4 hover:underline md:mr-6">Licensing</a>
      </li>
      <li>
          <a href="#" class="hover:underline">Contact</a>
      </li>
  </ul>
</footer>

</template>

<script>
export default {
  data() {
    return {
      items: [],
      newItemText: '',
      editingItem: null,
    };
  },
  methods: {
    addItem() {
      this.items.push({
        id: this.items.length + 1,
        text: this.newItemText, 
      });
      this.newItemText = '';
    },
    editItem(item) {
      this.editingItem = item;
    },
    saveItem() {
      this.editingItem = null;
    },
    cancelEdit() {
      this.editingItem = null;
    },
    deleteItem(item) {
      this.items = this.items.filter(i => i.id !== item.id);
    },
  },
};
</script>
