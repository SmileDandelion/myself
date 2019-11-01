<template>
  <div id="app">
    <button type="button" style="position: absolute;right: 0;top: 0" @click="print">打印</button>
    <router-view ref='printPage'/>
  </div>
</template>

<script>
export default {
  name: 'App',
  methods:{
    print(){
        //打印区域的内容
        var printContents = this.$refs['printPage'].$el.innerHTML
        //页面的所有内容
        var originalContents = document.body.innerHTML
                
        document.body.innerHTML = printContents
        window.print()
        document.body.innerHTML = originalContents
        //直接恢复页面可能会造成页面“假死”，可通过重新加载的方式恢复
        window.location.reload()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 595px;
  min-height: 842px;
  margin: auto;
  box-shadow: 0 0 0 1000px #333; 
}
</style>
