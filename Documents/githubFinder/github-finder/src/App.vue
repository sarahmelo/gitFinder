<template>
  <div id="app">

    <div class="container">
      <div class="card card-body">
        <h1>Pesquisar Usuários do github</h1>
        <p class="lead">Digite um nome para encontrar usuários e repositórios</p>
        <input @keyup="getUser" type="text" id="search" class="form-control" required>
      </div>
      <div class="row mt-3" v-if="user.length !== 0">
        <div class="col-md-4">
          <Profile :user="user"/>
        </div>
      </div>
    </div>  
  </div>
</template>

<script>
import axios from 'axios'
import Profile from './components/Profile.vue'

export default {
  name: 'App',
  components: {
    Profile
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

        axios.get(`${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
      ).then(({data}) => this.user = data)
      .catch(e => console.log(e))
    }
  }
}
</script>

