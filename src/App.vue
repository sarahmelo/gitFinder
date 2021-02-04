<template>
  <div id="app">

    <div class="container">
      
        <h5>  <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
                <path d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z"/>
              </svg> GitFinder
        </h5>
        <input v-model="search" type="text" id="search" class="form-control" placeholder="search" required>
      </div>
      <div class="row mt-3" v-if="user.length !== 0">
        <div class="col-md-4">
          <Profile :user="user"/>
          <div class="col-md-8">
          <Repo v-for="repo in repos" :repo="repo" :key="repo.id"/> <!-- repo.id irá guardar/identificar usuários pelo seu id git  -->
        </div>
        </div>
      
    </div>  
  </div>
</template>

<script>

import axios from 'axios';
import Profile from './components/Profile.vue';
import Repo from './components/Repo'

export default {
  name: 'App',
  components: {
    Profile,
    Repo
  },
  data () {
    return {
      github: {
        url: 'https://api.github.com/users',
        client_id: 'Iv1.7354bffa6e7f476d',
        client_secret: 'I6pxv/ZUkfcM/U1ZlzErR9hKx23JGdhvoERMZPL5zH8=',
        count: '7',
        sort: 'created asc'
      },
        user: [],
        repos: [],
        search: '' // search -> armazenar o value do input
      
    };
  },
  watch: {
     search(newValue, oldValue) {
          
        setTimeout(() => {
            this.handleKeyUp();
          },2000)
        
      }
    },
    
    //   search(newValue, oldValue) {
    //     if(oldValue) {
          
    //       setTimeout(() => {
    //         this.handleKeyUp();
    //       },3000)
          
        
    //     }
    //   }
    // },

  methods: {

    debounce(func, wait) {
      let timer; 
          clearTimeout(timer);
          timer = setTimeout(func, wait);

    },

    
    handleKeyUp() {
      this.debounce(this.makeRequest,2000)
      
    },

    makeRequest() {

        const { url, client_id, client_secret, count, sort} = this.github;

          axios
            .get(`${url}/${this.search}?client_id=${client_id}&client_secret=${client_secret}`)
              .then(({data}) => this.user = data);
          axios
            .get(`${url}/${this.search}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}
            &client_secret=${client_secret}`)
              
              .then(( {data} ) => (this.repos = data)); 

    }
  }
}

</script>

<style>

svg {
  margin-right: 4px;
}

h5 {
  
  color:#1F1F1F;
  font-family: 'Poppins', sans-serif;
  display: flex;
  align-content: center;
}

div#app{
  
  height: 100vh;
  width: 100vw;
  
  font-family: 'Open Sans', sans-serif;
  font-size: x-small;

  background: #CECECE;
  display: grid;
  align-items: center;
  place-content: center;
  overflow-y: auto;
}

div.container {
  
  align-items: center;
  display: flex;
  flex-direction: column;
  margin-top: auto;
  height: max-content;
}

input#search.form-control {
  
  width: auto;
  height: 24px;
  font-size: smaller;
  font-family: 'Open Sans', sans-serif;
  color: #1F1F1F;

  background-color: transparent;
  border-radius: 1rem;
  border-color: #1F1F1F;
  
}

div.col-md-8 {
  
  width: 320px;
  height: 170px;
  background: #080808;
  border-radius: 0 0 15px 15px;
  overflow: auto;
}

div.row.mt-3 {

  align-items: center;
  display: content;
  width: auto;
  height: auto;
  
}

</style>


