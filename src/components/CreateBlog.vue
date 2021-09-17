<template>
    <div class="blog-container">
        <h1> Create Blog </h1>
        <form @submit.prevent="createblg" autocomplete="off">
            <table>
            <tr>
                <td><label for="title"> Title </label></td>
                <td> : </td>
                <td><input type="text" id="title" v-model="values.title"/></td>
            </tr>
            <tr>
                <td><label for="description"> Description </label></td>
                <td> : </td>
                <td><input type="text" id="description" v-model="values.description"/></td>
            </tr>
            <tr><td colspan="3" style="text-align:center;"><input type="submit" id="subbtn"></td>
            </tr>
            </table>
        </form>

        <button @click="showbg='true'"> ShowBlogs </button>
        <ShowBlogs v-show="showbg=='true'"  />
    </div>
</template>

<script>
import ShowBlogs from './ShowBlogs'
import axios from 'axios'
export default{
name:'CreateBlog',
components: {
     ShowBlogs
    },
data(){
    return{
        showbg:false,
        values:[{
            title:'',
            description:''
        }],
    }
},
methods:{
    createblg(){
        axios.post('https://blog-d4917-default-rtdb.firebaseio.com/posts.json',{
            title:this.values.title,
            description:this.values.description
        }).then((response)=>{
            alert("Created Successfully");
            console.log(response);
        })
        .catch((error)=>{
         console.log(error);   
        })


    }
}
}
</script>

<style>
.blog-container{
    width:450px;
    margin:auto;
}
h1{
    text-align: center;
    background-color:cadetblue;
    border-radius: 10px;
    padding:10px;
}
label{
    font-size: 150%;
}
input{
   border:4px solid blanchedalmond;
   border-top: 0px;
   border-right: 0px;
   border-left: 0px;
   font-size:150%;
   margin:5%;
}
input:focus{
    outline:none;
}
#subbtn{
    border-radius: 5px;
    padding:7px 10px 7px 10px;
    border:1px solid black;
    background-color: cornflowerblue;
}
#subbtn:focus{
    border:2px solid black;
}
#subbtn:active{
    background-color: white;
}
#subbtn:hover{
    background-color: cornsilk;
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
</style>