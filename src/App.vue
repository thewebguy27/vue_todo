<template>
  <div id="app">
    <div id="nav">
   <Header/>
    </div>
    <router-view/>
  </div>
</template>
<script>
import Header from './components/layouts/Header'
export default {
  name:"app",
  components:{
    Header
  }
}
</script>