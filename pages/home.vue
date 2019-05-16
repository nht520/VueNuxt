<template>
  <div class="container">
      <NuxtLink to="/">
      &lt; Prev
    </NuxtLink>
    <a  class="disabled">
      &lt; Prev
    </a>
    <span>{{ page }}/{{ totalPages }}</span>
      <NuxtLink to="/">
      Next &gt;
    </NuxtLink>
    <a  class="disabled">
      Next &gt;
    </a>
    <ul>
      <li v-for="user in users" :key="user.id">
        <img :src="user.avatar" class="avatar">
        <span>{{ user.first_name }} {{ user.last_name }}</span>
      </li>
    </ul>
    <p>
      <NuxtLink to="/">
        Back home
      </NuxtLink>
    </p>
  </div>
</template>

<script>
export default {
  // Called to know which transition to apply
  transition(to, from) {
    if (!from) return 'slide-left'
    return +to.query.page < +from.query.page ? 'slide-right' : 'slide-left'
  },
  
  async asyncData({ query }) {
    const page = +query.page || 1
    const data = await fetch(`https://reqres.in/api/users?page=${page}`).then(res => res.json())
    return {
      page: +data.page,
      totalPages: data.total_pages,
      users: data.data
    }
  }
}
</script>

<style scoped>
a.disabled {
  color: #ccc;
}
ul {
  margin: auto;
  padding: 0;
  width: 100%;
  max-width: 400px;
  padding-top: 40px;
}
li {
  list-style-type: none;
  width: 400px;
  border: 1px #ddd solid;
  overflow: hidden;
}
li img {
  float: left;
  width: 100px;
  height: 100px;
}
li span {
  display: inline-block;
  padding-top: 40px;
  text-transform: uppercase;
}
</style>
