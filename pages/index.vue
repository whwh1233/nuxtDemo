<template>
  <div class="container">
    <div class="links">
      <a href="/detail" rel="noopener noreferrer" class="button--green">
        detail
      </a>
      <a href="/activity" rel="noopener noreferrer" class="button--green">
        activity
      </a>
      <a href="/parent" rel="noopener noreferrer" class="button--green">
        parent
      </a>
    </div>

    <div class="message">
      <br />
      <p>{{ msg }}</p>
    </div>
    <div v-for="(item, index) in post.data.c2cSkuList" :key="index" @click="to(item.c2cSkuId)">
      <div>{{ item.c2cSkuId }}</div>
      <img :src="item.coverUri" class="img" />
      <div>{{ item.content }}</div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    to(c2cSkuId) {
      console.log('点击商品')
      console.log(c2cSkuId)
    }
  },

  async asyncData({ $axios }) {
    let msg = '空'
    const post = await $axios.$post('http://apidev.bangbangtown.cn/o/cc/2.0/uic2c/home')
    msg = await $axios.$post('http://apidev.bangbangtown.cn/o/cc/1.0/uic2c/getSellC2cSku', {
      c2cSkuId: 1001168
    })
    const activity = await $axios.$post('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6430')
    return { post, msg, activity }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.img {
  width: 200px;
  height: 200px;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
