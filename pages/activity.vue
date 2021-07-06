<template>
  <div class="container">
    <div class="links">
      <a href="/index" rel="noopener noreferrer" class="button--green">
        index
      </a>
    </div>
    <div>{{ activityInfo }}</div>
    <div class="message">
      <br />
      <h2>{{ activityInfo.title }}</h2>
    </div>
    <section v-show="dataList" class=" cfix">
      <div v-for="(tplData, tplIndex) in dataList" :key="tplIndex">
        <h5>模块：{{ tplData.tpl }}</h5>
        <div v-if="tplData.tpl === 'm51' || tplData.tpl === 'm73' || tplData.tpl === 'm67' || tplData.tpl === 'm66' || tplData.tpl === 'm55'">
          <component :is="tplData.tpl" :tpl-data="tplData" :activityId="activityInfo.id"></component>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  methods: {},

  async asyncData({ $axios }) {
    const activity = await $axios.$post('https://apidev.bangbangtown.cn/o/uc/1.0/uiww/activity?id=6412')
    let data = activity.data
    let dataList = data.tplDataList
    let activityInfo = data.activityInfo
    return { dataList, activityInfo }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.links {
  padding-top: 15px;
}
</style>
