<template>
    <div>
        <form @submit.prevent="addNewTwit()">
               <div class="form-group">
                   <label for="">Content</label>
                   <textarea v-model="twitContent" id="" cols="30" rows="5" class="form-control" :class="errorClass" :disabled="disableEditing"></textarea>
                   <p>Character: {{twitContentCharacter}}/40</p>
                </div> 
               <div class="form-group">
                   <label for="">Status</label>
                   <select v-model="twitStatus" id="" cols="30" rows="5" class="form-control">
                       
                       <option value="draft">Draft</option>
                       <option value="published">Published</option>
                   </select>
                </div> 
               <div class="form-group">
                   <button type="submit" >Submit</button>
                </div> 
        </form>
    </div>
</template>


<script>
export default {
    data(){
        return{
            twitContent:'',
            twitStatus: 'draft',
            errorClass: '',
            disableEditing:false
        }
    },
    watch:{
        twitContentCharacter(newContentLength){
            if(newContentLength >= 40){
                 this.errorClass = 'border-danger'; this.disableEditing = true;
            }
        }
    },
    computed:{
        twitContentCharacter(){
            return this.twitContent.length;
        }
    },
    methods:{
        addNewTwit(){
            let data = {
                twitContent: this.twitContent
            }
            
          
            this.$emit('add-twit', data);
        }
    }
}
</script>

<style>

</style>