<template>
  <input type="text" v-model="userName" placeholder="Name">
  <input type="password" v-model="userPass" placeholder="Password">
  <input type="email" v-model="userEmail" placeholder="Email">
  <p className="error">{{ error }}</p>
  <button @click="sendData()">send</button>

  <p>{{ users }}</p>
</template>

<script>
export default {
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
