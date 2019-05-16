<template>
  <div class="container">
    <p>About Page</p>
    <p>It should take 5 seconds for the loader to disappear</p>
    <p>
      It should take 5 seconds for the route to change after you
        click here
    </p>
    <nuxt-link to="/">返回</nuxt-link>
  </div>
</template>

<script>
export default {
  transition(to, from) {
    if (!from) return 'slide-left'
    return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
  },
  asyncData() {
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({})
      })
    })
  },
  mounted() {

  },
  methods: {
  }
}
</script>

<style scoped>
.link {
  cursor: pointer;
  text-decoration: underline;
}
.container {
  font-size: 20px;
  text-align: center;
  padding-top: 100px;
}
</style>
