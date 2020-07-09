<template>
  <div id='ask'>
    <button id='askButton' type='button' @click='askWord'>点击获取大佬人生经验</button>
    <p id='mes'>{{ mes }}</p>
  </div>
</template>

<script>
export default {
  name: 'ask',
  data: function () {
    return {
      mes: ''
    }
  },
  methods: {
    askWord: function () {
      this.$axios
        .get('https://api.scuter.icu/test/word')
        .then(async function (Response) {
          // 这里的this由于是在function(Response)内，所以并没有指向askWord对象
          // 我也不知道这样要怎样才能使用到data中的mes，所以忍痛抛弃Vue响应
          // 用js的DOM模型方法直接改变元素的内容
          if (Response.data['code']) {
            // this.mes = '请求失败'
            document.getElementById('mes').innerHTML = '请求失败'
            document.getElementById('askButton').innerHTML = '获取失败，点击再来一次'
          } else {
            // this.mes = Response.data['word']
            document.getElementById('mes').innerHTML = Response.data.word
            document.getElementById('askButton').innerHTML = '点击获取大佬人生经验'
          }
          await this.$nextTick()
        })
        .catch(function () {
        })
    }
  }
}
</script>

<style>

</style>
