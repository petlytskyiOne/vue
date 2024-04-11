<template>
  <h3>{{ info }}</h3>
  <p>{{ someInfo }}</p>
</template>

<script>
export default {
  data() {
    return {
      info: "Title!",
      someInfo: 'Anons of message'
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
