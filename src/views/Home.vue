<template>
  <div>
    <h1>匿名板3</h1>
    <n-form :label-width="80" :model="formValue" :rules="rules" :size="size" ref="formRef">
      <n-form-item label="说什么吧：" path="formValue:content">
        <n-input v-model="formValue.content" placeholder="很久很久以前..."/>
      </n-form-item>
      <n-form-item>
        <n-button @click="handleValidateClick" attr-type="button">验证</n-button>
      </n-form-item>
    </n-form>

    <pre>
  {{  JSON.stringify(formValue, 0, 2) }}
  </pre>
  </div>
</template>

<script>
import {defineComponent, ref} from 'vue'
import {useMessage} from 'naive-ui'
export default defineComponent({name: "Home"}, {
  setup() {
    const formRef = ref(null)
    const message = useMessage()
    return {
      formRef,
      size: ref('medium'),
      formValue: ref({
        content: ''
      }),
      rules: {
        content: {
          required: true,
          trigger: ['input']
        }
      },
      handleValidateClick() {
        formRef.value.validate((errors) => {
          if (!errors) {
            message.success('Valid')
          } else {
            console.log(errors)
            message.error('Invalid')
          }
        })
      }
    }
  }
})
</script>

<style scoped>

</style>