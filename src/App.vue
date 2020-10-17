<template>
  <div>
    <UserProfile></UserProfile>
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile";
export default {
  name: 'App',
  components:{
    UserProfile
  }
  
}
</script>

<style>
#app{
  padding-top: 40px;
}
</style>
