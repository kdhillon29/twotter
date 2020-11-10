<template>
<div class="user-panel">
    <div class="uprofile">
    <h3>@{{user.username}}</h3>
    <h4>{{fullname}} <strong class="badge" v-if="user.isAdmin">Admin</strong></h4>
    
    <h5>Followers:{{followers}} </h5>
    <div class ="add-twoot">
        <label for="tinput">Twoot</label>
        <textarea rows="3" id="tinput" />
        <label for="ttype">Type:</label>
        <select name="twoottype" id="ttype">
          <option v-for="(op,index) in twootType" :key="index" :value="op.type">{{op.name}}</option>

        </select>
        <button>Twoot</button>

    </div>
    </div>

    <div class="twoot-list" > 
       <twoot-item
          v-for="twoot in twoots"
          :key="twoot.id"
          :username="user.username"
          :twoot="twoot"
          @favourite="toggleFav" />
    </div>
</div>
</template>

<script>
import TwootItem from './TwootItem.vue'
export default {
  name: 'UserProfile',
  components:{
        TwootItem
  },
  data(){
    return{
        twootType:[{
            type:'draft',
            name:'Draft'
        },
        {
            type:'instant',
            name:'Instant Twoot'
        }
        ],
        
        followers:0,
        user:{
              username:'_kanwardhillon',
              fname:"Kanwar",
              lname:'Dhillon',
              isAdmin:true,
              email:"kdhillon469@gmail.com",
              
          },
        twoots:[
        {id:1,
            content:"A wonderful Twoot"
        },
        { id:2,
          content:" marvellous Twoot"
        }
        ]
    }
    },
    computed:{
        fullname(){
            return `${this.user.fname} ${this.user.lname}`
        }

    },
    mounted(){
        this.followers+=1
    },
    methods:{
      toggleFav(id){
          console.log('fav twoot is',id)
          window.alert(`my fav twoot is ${id}`)
      }
    },
    watch:{
        followers(newCount,oldCount){
            if(newCount>oldCount){
                console.log('followers increased to ',this.followers)
            }
            else {
            console.log('followers are same')
           }

        }
    }
  
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-panel{
    display:flex;
    justify-content: flex-start;
    padding:10px;
    background-color:lightslategray;
    height:100vh;
    
    
   
}
 @media only screen and (max-width: 600px) {
     .user-panel{
         flex-direction:column;
     }
    }

.twoot-list{
     flex:3 1 auto; 
     display:flex;
    flex-direction: column;
    margin:2px;
    padding:10px;
}
.uprofile{
    background-color:linen;
    border:1px solid white;
    border-radius: 20px;
    padding:5px ;
    margin:10px 20px;
    flex: 1 0 100px;
    height:fit-content;
    

}
.badge{
     background-color:rebeccapurple;
     font:caption;
     padding:2px 10px;
     border-radius:5px;
     margin-right:auto;
}
p{
    margin-top:-20px;
    font:initial
}
.add-twoot{
    display:flex;
    flex-direction: column;
    padding:2px ;
}
.add-twoot > button{
   margin:5px auto;
   padding:5px 10px;
   
}
</style>
