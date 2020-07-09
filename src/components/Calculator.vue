<template>
  <div id='cal'>
    <form>
      <input
        type='number'
        v-model='num1'
        @change='calculate'
      />
      <!--
        input标签，用v-model绑定了变量num1，
        同时绑定了事件chang响应calcula函数
      -->
      <select
        v-model='cal'
        @change='calculate'
      >
      <!--
        select标签，用v-model绑定了变量cal，
        同时绑定了事件chang响应calcula函数
      -->
        <option value='+'>+</option>
        <option value='-'>-</option>
        <option value='*'>×</option>
        <option value='/'>÷</option>
      </select>
      <input
        type='number'
        v-model='num2'
        @change='calculate'
      />
      <br>
      <p>答案是：<output>{{ ans }}</output></p>
      <!--
        将output标签内嵌在p标签内，保持默认的inline显示
        其实就是懒得加css给output排版。。。
      -->
    </form>
  </div>
</template>

<script>
export default {
  name: 'cal',
  data: function () {
    return {
      num1: 0,
      num2: 0,
      cal: '+',
      ans: 0
    }
  },
  methods: {
    calculate: async function () {
      switch (this.cal) {
        case '+':
          this.ans = Number(this.num1) + Number(this.num2)
          break
        case '-':
          this.ans = this.num1 - this.num2
          break
        case '*':
          this.ans = this.num1 * this.num2
          break
        case '/':
          this.ans = this.num1 / this.num2
          break
      }
      await this.$nextTick()
    }
  }
}
</script>

<style>
</style>
