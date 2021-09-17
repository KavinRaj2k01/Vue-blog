<template>
   <div>
       <button @click="showb">Click to Load Blogs </button>
    <div v-for="post in posts" :key="post.title"  >
        <div class="blog-container"><h2> {{post.title}} </h2>
        <p> {{post.description}}</p>
        <h3><hr/></h3></div>
    </div>
   </div>
</template>

<script>
import axios from 'axios'
export default{
name:'ShowBlogs',
data(){
    return{
        posts:''
    }
},
methods:{
    showb(){
        axios.get('https://blog-d4917-default-rtdb.firebaseio.com/posts.json',{
        }).then((response)=>{
            console.log(response.data);
            this.posts=response.data;
        })
        .catch((error)=>{
         console.log(error);   
        })
    }
}
}
</script>

<style scoped>
h2{
    background-color:floralwhite;
    text-align: center;
    border:1px solid darksalmon;
    border-radius: 3px;
    padding: 3px;
}
p{
    text-align: center;
    padding: 3px;
    font-family: Georgia, serif;
}
button{
    font-size:130%;
    border-radius: 5px;
    padding:7px 10px 7px 10px;
    border:1px solid brown;
    background-color: beige;
}
button:active{
    background-color: darkkhaki;
}
.blog-container{
    background-color:bisque;
    
}

</style>