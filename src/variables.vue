<template>
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>

  <button type="button" @click="userData()">send</button>
  <button type="button" @mouseenter="this.someInfo = 'Some new'">send</button>
</template>

<script>
export default {
  data() {
    return {
      info: "Title!",
      someInfo: 'Anons of message'
    }
  },
  methods: {
    userData() {
      this.info="Some new"
      this.someInfo="Some new1"
    }
  }
}
</script>

<style scoped>
h3 {
  font-weight: lighter;
}

p {
  color: rgb(203, 31, 31);
}
</style>
