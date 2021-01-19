<template>
  <div id="app">

    <div class="container">
      
        <h5> GitFinder</h5>
        <!-- <p class="lead">Digite um nome para encontrar usuários e repositórios</p> -->
        <input @keyup="getUser" type="text" id="search" class="form-control" placeholder="search" required>
      </div>
      <div class="row mt-3" v-if="user.length !== 0">
        <div class="col-md-4">
          <Profile :user="user"/>
        </div>
        <div class="col-md-8">
          <Repo v-for="repo in repos" :key="repo" :repo="repo"/>
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
        repos: []
    };
  },
  methods: {
  

    getUser(e) {
      const user = e.target.value;
      const { url, client_id, client_secret, count, sort} = this.github;

        axios
          .get(`${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`)
          
            .then(({data}) => this.user = data);

        axios
          .get(`${url}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}
          &client_secret=${client_secret}`)
            
            .then(( {data} ) => (this.repos = data));

      
    }
  }
}
</script>

<style>

h5 {
  color: #FC5520;
  font-family: 'Poppins', sans-serif;
}

div#app{
  height: 100vh;
  width: 100vw;
  overflow-y: auto;

  background: #172634;
}

div.container {
  align-items: center;
  display: flex;
  flex-direction: column;
}

input#search.form-control {
  height: 30px;
  font-size: small;
  font-family: 'Open Sans', sans-serif;;

  background: #0F1C28;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25), 2px 0px 4px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  border: none;
  width: auto;

}

div.col-md-8 {
  width: auto;
  height: 300px;
  background: #0F1C28;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.4);
  border-radius: 3px;
  content-visibility: auto;
  overflow: auto;
}

div.row.mt-3 {
  justify-content: center;
  align-items: center;
  display: flex;
  
}

</style>