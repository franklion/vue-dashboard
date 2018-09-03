<template>
  <div class="hello">
    <a href="#" @click.prevent="signout">登出</a>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods: {
    signout() {
      const api = `${process.env.VUE_APP_APIPATH}/logout`
      this.$http.post(api).then((response) => {
        console.log(response.data)

        if (response.data.success) {
          this.$router.push('/login')
        }
      })
    },
  },
}
</script>

