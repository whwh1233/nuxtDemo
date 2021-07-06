<style scoped>
.parent__info {
  height: 400px;
  overflow: auto;
}
</style>

<template>
  <div class="container ">
    <div class="links">
      <a href="/" rel="noopener noreferrer" class="button--green">
        index
      </a>
    </div>
    <Child ref="child" :api="api" />
    <div class="parent__info">
      1111
      <!-- <p>{{ res }}</p> -->
    </div>

    <!-- <div class="detail">
      {{ detail }}
    </div> -->

    <div class="parent__info">{{ res.data.tplDataList[5] }}</div>
    <div class="parent__info">{{ res.data.tplDataList[9] }}</div>
    <div class="parent__info">{{ res.data.tplDataList[12] }}</div>
    <!-- <div>{{ activity }}</div> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      api: ''
    }
  },
  methods: {},

  async asyncData({ $axios }) {
    // const res = 'null'
    const res = await $axios.$post('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430')
    // const detail = await $axios.$post('http://apidev.bangbangtown.cn/o/cc/1.0/uic2c/getSellC2cSku', {
    //   c2cSkuId: 1001168
    // })
    const detail = await $axios.$post('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430')

    let api = 'https://api.nuxtjs.dev/mountains'
    api = res.data.tplDataList[5].tabInfo[0].id
    // this.$refs.child.setData()
    return { res, detail, api }
  }
}
</script>
