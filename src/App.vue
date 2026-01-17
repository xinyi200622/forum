<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <validate-input :rules="emailRules" v-model="emailVal" placeholder="请输入邮箱地址"></validate-input>{{ emailVal }}
    <div class="form-text" v-if="emailRef.error">{{ emailRef.message }}</div>
    <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <validate-input type="password" placeholder="请输入密码" :rules="passwordRules" v-model="passwordVal"></validate-input>
  </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue'
import '../bootstrap-5.3.0-alpha1-dist/css/bootstrap.min.css'
import '../bootstrap-5.3.0-alpha1-dist/js/bootstrap.min.js'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const currentUser: UserProps = {
  isLogin: true,
  name: 'viking'
}
const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是test1的专栏，有一段非常有意思的简介，可以更新一下欧',
    avatar: 'https://p5.ssl.qhimgs1.com/t012ca48704a4fc9285.png'
  },
  {
    id: 2,
    title: 'test2的专栏',
    description: '这是的test2专栏，有一段非常有意思的简介，可以更新一下欧',
    avatar: 'https://p5.ssl.qhimgs1.com/t012ca48704a4fc9285.png'
  },
  {
    id: 3,
    title: 'test3的专栏',
    description: '这是的test3专栏，有一段非常有意思的简介，可以更新一下欧',
    avatar: 'https://p5.ssl.qhimgs1.com/t012ca48704a4fc9285.png'
  },
  {
    id: 4,
    title: 'test4的专栏',
    description: '这是的test4专栏，有一段非常有意思的简介，可以更新一下欧',
    avatar: 'https://p5.ssl.qhimgs1.com/t012ca48704a4fc9285.png'
  }
]
export default defineComponent({
  name: 'App',
  components: {
    GlobalHeader,
    ValidateInput
  },
  setup () {
    const emailVal = ref('')
    const emailRules: RulesProp = [
      { type: 'required', message: '电子邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]
    const emailRef = reactive({
      val: '',
      error: false,
      message: ''
    })
    const passwordVal = ref('')
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' },
      { type: 'password', message: '请输入长度 8-20 位，包含大写字母 + 小写字母 + 数字 + 特殊符号（至少各 1 位），排除空格的密码' }
    ]
    const passwordRef = reactive({
      val: '',
      error: false,
      message: ''
    })
    return {
      list: testData,
      currentUser,
      emailRef,
      ValidateInput,
      emailRules,
      emailVal,
      passwordVal,
      passwordRules,
      passwordRef
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
