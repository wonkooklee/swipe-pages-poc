<template>
  <div class="hello">
    <h2>{{ data.id }}</h2>
    <p>{{ data.title }}</p>
  </div>
</template>

<script>
export default {
  name: 'CompC',
  data () {
    return {
      data: {}
    }
  },
  mounted () {
    this.fetching()
  },
  methods: {
    fetching () {
      fetch('https://jsonplaceholder.typicode.com/todos/3')
      .then(res => res.json())
      .then(json => this.data = json)
    }
  }
}
</script>

<style scoped lang="scss">
div {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: tomato;
  height: 600px;

  h2 {
    margin: 0;
    color: #fff;
    font-size: 60px;
  }

  p {
    color: #fff;
    font-size: 24px;
  }
}
</style>
