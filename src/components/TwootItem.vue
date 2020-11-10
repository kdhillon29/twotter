<template>
  <div class="twoot-item" @click="myFav(twoot.id)">
    <div class ="twoot-item-user">
        @{{username}}
    </div>
    <div class=twoot-item-content>
        <p>{{twoot.content}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TwootItem',
  props: {
    username: {
       type: String,
       required:true
    },
  twoot: {
       type: Object,
       required:true
    }
 },
 methods:{
     myFav(id){
         this.$emit("favourite",id)
     }
 }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3{
    color:green;
}
.twoot-item{
    padding:2px ;
    background-color: white;
    border-radius: 5px;
    border:1px solid grey;
    box-sizing: border-box;
    cursor:pointer;
    margin-bottom:5px;
    
    transition:all .25s ease;

}
.twoot-item:hover{
    transform:scale(1.1,1.1)
}
.twoot-item-user{
    font-weight: bold;
}
.twoot-item-content{
    margin-top:-10px;
    color:lightcoral
}

</style>
