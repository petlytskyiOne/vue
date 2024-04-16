<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error">{{ error }}</p>
  <button @click="sendData()">send</button>

  <div v-if="users.length == 0" className="user">
    We don't have any users!
  </div>

  <div v-else-if="users.length == 1" className="user">
    Users has One element!
  </div>

  <div v-else className="user">
    Array has more than one element!
  </div>

  <User v-for="(el, index) in users" :key="index" :user="el" :index="index" :deleteUser="deleteUser" />
  <!-- event processing for the entire object without a button -->
  <!-- @click="deleteUser(index)" -->

  <!-- transferred to components as an object -->
  <!-- <div v-for="(el, index) in users" :key="index" className="user">
    <h3>{{ el.name }}</h3>
    <p>{{ el.email }} - <b>{{ el.pass }}</b></p>
  </div> -->
</template>

<script>

import User from './components/User.vue';

export default {
  components: { User },
  data() {
    return {
      users: [],
      error: '',
      userName: '',
      userPass: '',
      userEmail: ''
    }
  },
  methods: {
    sendData() {
      if (this.userName=='') {
        this.error='name not entered !!!';
        return;
      } else if (this.userEmail=='') {
        this.error='email not entered !!!';
        return;
      } else if (this.userPass=='') {
        this.error='pass not entered !!!';
        return;
      }

      this.error='';

      this.users.push({
        name: this.userName,
        pass: this.userPass,
        email: this.userEmail
      })
    },
    deleteUser(index) {
      this.users.splice(index, 1);
    }
  }
}
</script>

<style scoped>
input {
  display: block;
  margin-bottom: 10px;
  border-radius: 3px;
  border: 1px solid silver;
  outline: none;
  padding: 10px 15px;
  background: #fafafa;
  color: #333;
}

button {
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background: #6cd670;
  color: #167f3d;
  font-weight: bold;
  cursor: pointer;
  transition: transform 500ms ease;
}

button:hover {
  transform: translateY(-5px);
}

.user {
  width: 500px;
  margin-top: 20px;
  border: 1px solid silver;
  background: #e3e3e3;
  color: #222;
  padding: 20px;
  border-radius: 5px;
}
</style>
