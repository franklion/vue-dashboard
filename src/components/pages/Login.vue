<template lang="pug">
  .page-login
    form.form-signin(@submit.prevent="signin")
      h1.h3.mb-3.font-weight-normal 請先登入
      label.sr-only(for='inputEmail') Email address
      input#inputEmail.form-control(type='email', v-model="user.username" placeholder='Email address', required='', autofocus='')
      label.sr-only(for='inputPassword') Password
      input#inputPassword.form-control(type='password', v-model="user.password" placeholder='Password', required='')
      .checkbox.mb-3
        label
          input(type='checkbox', value='remember-me')
          |  Remember me
      button.btn.btn-lg.btn-primary.btn-block(type='submit') Sign in
      p.mt-5.mb-3.text-muted &copy; 2017-2018

</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      user: {
        username: '',
        password: '',
      },
    }
  },
  methods: {
    signin() {
      const api = `${process.env.VUE_APP_APIPATH}/admin/signin`
      this.$http.post(api, this.user).then((response) => {
        console.log(response.data)

        if (response.data.success) {
          this.$router.push('/')
        }
      })
    },
  },
}
</script>

<style lang="sass" scoped>
html,
body 
	height: 100% 
body 
	display: -ms-flexbox 
	display: flex 
	-ms-flex-align: center 
	align-items: center 
	padding-top: 40px 
	padding-bottom: 40px 
	background-color: #f5f5f5 
.form-signin 
	width: 100% 
	max-width: 330px 
	padding: 15px 
	margin: auto 
	.checkbox 
		font-weight: 400 
	.form-control 
		position: relative 
		box-sizing: border-box 
		height: auto 
		padding: 10px 
		font-size: 16px 
		&:focus 
			z-index: 2 
	input[type="email"] 
		margin-bottom: -1px 
		border-bottom-right-radius: 0 
		border-bottom-left-radius: 0 
	input[type="password"] 
		margin-bottom: 10px 
		border-top-left-radius: 0 
		border-top-right-radius: 0 

</style>
