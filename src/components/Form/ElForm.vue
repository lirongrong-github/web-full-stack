<template>
  
  <div>

    <slot></slot>

  </div>

</template>

<script>
  
  export default {

    // 传递Form实例给后代, 可隔代传值 比如formItem得校验
    provide() {

      return {

        form: this

      }

    },

    props: {

      model: {

        type: Object,

        required: true

      },

      rules: {

        type: Object

      }

    },

    methods: {
     
      validate (cb) {

        // map 的结果为Promise数组
        const tasks = this.$children
          .filter( item => item.prop )
          .map( item => item.validate() )

        // 所有任务全部成功才算通过校验
        Promise.all( tasks )
          .then( () => cb(true) )
          .catch( () => cb(false) )

      }

    }

  }

</script>

<style scoped lang="scss"></style>