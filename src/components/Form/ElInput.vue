<template>

  <div>

    <!-- {{ $attrs }} 对父组件穿过类得props意外得自定义属性 得集合 -->
    <!-- 自定义组件想要实现v-model 必须通过 :value @input -->
    <input :value=" value " @input=" onInput " v-bind="$attrs">    

  </div>

</template>

<script>
  
  export default {

    name: 'ElInput',

    // 避免顶层容器继承属性
    inheritAttrs: false,
    
    props: {

      value: {

        type: String,
        default: ''

      }

    },

    methods: {
     
      onInput(e) {

        // 通知父组件数值变换
        this.$emit( 'input', e.target.value )

        // 通知父组件校验
        this.$parent.$emit( 'validate' )

      }

    }
  
  }

</script>

<style scoped lang="scss"></style>