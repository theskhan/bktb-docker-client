<template>
  <div>
      <div v-for="user in users">
          <p>Name: {{user.name}} (<b>{{user.id}}</b>)</p>
          <p>Address: {{user.address}}</p>
          <p>Email: {{user.email}}</p>
          <p>About: {{user.about}}</p>
          <img width="64" height="64" :src="user.profileUrl" />
          <hr/>
      </div>
  </div>
</template>

<script>
import config from '../config';
import axios from 'axios';

export default {
  name: 'users',
  data () {
    return {
      users: null,
      port: config.apiBaseUrl
    }
  },
  mounted () {
      var that = this;

      axios.get(config.apiBaseUrl + "user").then(function(response) {
          that.users = response.data;
      })
  }
}
</script>

<style scoped>
    p {
        margin: 3px;
        padding: 3px;
    }
</style>
