<template>
  
  <div>

    <label v-if=" label ">
      
      {{ label }}
    
    </label>

    <slot></slot>

    <!-- 校验信息 -->
    <p v-if=" errorMessage ">
      
      {{ errorMessage }}

    </p>

  </div>

</template>

<script>

  import Schema from 'async-validator'

  export default {

    props: {


      label: {

        type: String,

        default: ''

      },

      prop: String

    },

    inject: [ 'form' ],

    data () {

      return {

        errorMessage: ''

      }

    },

    mounted() {
     
      // 监听校验事件， 并执行监听
      this.$on( 'validate', () => {

        this.validate()

      })

    },

    methods: {
      
      validate () {

        // 执行校验
        // 1. 获取校验规则
        const rules = this.form.rules[this.prop]

        // 2. 获取数据
        const value = this.form.model[this.prop]

        //3. 执行校验
        const desc = {

          [this.prop]: rules

        }

        const schema = new Schema(desc) 

        // 返回得Promise<boolean>
        return schema.validate( { [this.prop]: value }, errors => {

          if ( errors ) {

            // 有错误信息给到errorMessage
            this.errorMessage = errors[0].message

          } else {

            // 没错但可能以前有错， 多以要清除错误信息
            this.errorMessage = ''

          }

        })

      }

    }

  }
</script>

<style scoped lang="scss"></style>