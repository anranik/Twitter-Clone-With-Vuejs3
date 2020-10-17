<template>
    <div class="container">
    <div class="row">
      <div class="col-md-3">
        <div class="card">
          <div class="card-body">
            <h4>@{{user.userName}} - {{fullName}}</h4>
        <p>{{followers}} <button v-if="showFollowButton" @click="followUser()">follow</button>  <button v-if="showUnfollowButton" @click="unfollowUser()">UnFollow</button> </p>

        <hr />
        <NewTwit @add-twit="onClickChild"></NewTwit>
          </div>
          <!-- /.card-body -->
        </div>
        <!-- /.card -->
      </div>
      <!-- /.col-md-3 -->
      <div class="col-md-9">
        <div class="card" v-for="twit in user.twits" :key="twit.id">
          <div class="card-body">
            <h5>@{{user.userName}}</h5>
            <h4>{{twit.content}}</h4>
          </div>
          <!-- /.card-body -->
            
        </div>
        <!-- /.card -->
      </div>
      <!-- /.col-md-9 -->
    </div>
    <!-- /.row -->
  </div>
</template>


<script>
import NewTwit from './NewTwit'
export default {
    name: "UserProfile",
    components: {NewTwit},
    data(){
    return{
      followers:20,
      showFollowButton:true,
      showUnfollowButton: false,
      user:{
        userName: 'anranik',
        firstName: 'Anowar',
        lastName: 'Hossen',
        email:'anrctg@gmail.com',
        isAdmin: true,
        twits:[
          {id:1, content:'My very first twit'},
          {id:2, content:'Life is beautiful'},
          {id:3, content:'You always need me'},
        ]
      }
    }
  },
  watch:{
      followers(newFollowers, oldFollowers){
          console.log(`Old followers: ${oldFollowers} - New followers: ${newFollowers}`)
      }
  },
  computed:{
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods:{
    followUser(){
      this.followers++;
      this.showFollowButton = false
      this.showUnfollowButton = true
    },
    unfollowUser(){
      this.followers--;
      this.showFollowButton = true
      this.showUnfollowButton = false
    },
    onClickChild(data){ 
      let newTwit = {
        id: this.user.twits.length +1,
        content: data.twitContent
      }
      this.user.twits.push(newTwit);
    }
  }
}
</script>



<style >
.card{
  margin-bottom: 10px;
}
</style>