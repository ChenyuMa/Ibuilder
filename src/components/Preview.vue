<template>
  <div class="preview-contianer">
    <component :is="pageData.name" :com-data="pageData"></component>
  </div>
</template>
<script>
  import queryString from "@/utils/queryString.js"
  export default {
    data () {
      return {
      }
    },
    methods: {
      loadData() {
        this.axios.get('/centaur/page/getById?' + this.getLoginInfo())
          .then((res) => {
            let data = JSON.parse(res.data.content);
            this.$store.commit("addPage", !data ? new Page({ elements: [], }) : data)
          })
      },
      getLoginInfo () {
        return window.location.href.split('?')[1]
      }
    },
    created () {
      this.axios.get('/centaur/page/getDesignedList?accessToken=utry-ca41c21f055b11e8b2c9000c2907a862')
        .then((res) => {
          this.$store.state.allPageList = res.data
        })
      this.loadData()
    },
    computed: {
      pageData () {
        let pageInfo = this.$store.state.previewPage
        return pageInfo
      }
    }
  }
</script>
<style lang="less">
.preview-contianer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
