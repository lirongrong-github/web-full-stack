<template>
  
  <div>

    <ElForm :model="model" :rules="rules" ref="loginForm">

      <ElFormitem label="用户名" prop="username">
        
        <ElInput v-model="model.username" type="text"></ElInput> 

      </ElFormitem>
      
      <ElFormitem label="密码" prop="password">

        <ElInput v-model="model.password" type="password"></ElInput>

      </ElFormitem>

      <ElFormitem>
        
        <button @click=" onLogin ">登录</button>

      </ElFormitem>

    </ElForm>
    {{ model }}

  </div>

</template>

<script>

  import ElForm from './ElForm'
  import ElFormitem from './ElFormitem'
  import ElInput from './ElInput'
  
  export default {
    
    components: {

      ElForm,
      ElFormitem,
      ElInput,

    },

    data() {
     
      return {
    
        model: {

          username: 'lili',
          password: '123'

        },

        rules: {

          username: [{ required: true, message: '用户名必填' }],
          password: [{ required: true, message: '密码必填' }]

        }

      }
    
    },

    methods: {
      
      onLogin () {

        this.$refs.loginForm.validate( isValid => {

          if (isValid) alert('validate done')

          else alert('validate error')

        })

      }

    }
  
  }

</script>

<style scoped lang="scss"></style>