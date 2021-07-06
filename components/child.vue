<style scoped>
.child__info {
  height: 400px;
  overflow: auto;
}
</style>

<template>
  <div>
    <div>zi</div>
    <div class="child__info">{{ message[1] }}</div>
    <div class="child__info">{{ message[2] }}</div>

    <!-- <div class="cycle">
      <div class="cycle__el" v-for="(e,i)in message" :key="i">
        <div>e</div>
      </div>
    </div> -->
    <div>{{ delay }}</div>
  </div>
</template>

<script>
export default {
  props: {
    api: String
  },
  data() {
    return {
      mountains: {},
      delay: 'delay 3000 ms',
      message: {}
    }
  },
  methods: {
    async setData() {
      this.mountains = await fetch('https://api.nuxtjs.dev/mountains').then(res => res.json())
      // this.mountains = await fetch('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430').then(res => res.json())

      const sleep = ms => new Promise(r => setTimeout(r, ms))

      // await sleep(3000)
      this.delay = 'okkkkkkk'
    }
  },
  async fetch() {
    // let res = await $axios.$post('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430')
    console.log(this.api)

    let apiapi = 'https://m.wanwustore.cn/o/uc/1.0/uiww/activity?id=' + this.api
    console.log(apiapi)
    // this.mountains = await fetch('https://api.nuxtjs.dev/mountains').then(res => res.json())
    this.mountains = await fetch(apiapi).then(res => res.json())
    this.message = this.mountains.data.tplDataList
    // // this.mountains = await fetch('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430').then(res => res.json())
    // const sleep = ms => new Promise(r => setTimeout(r, ms))
    // // await sleep(3000)
    this.delay = 'okkkkkkk'
    // this.mountains = [1, 2, 3]
    // console.log('-----------------------------')
    // console.log(res)
    // console.log('-----------------------------')
    // return { res }
    // let res = '12'
    // return { res }
  }
}
</script>
