<template>
   <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col></b-col>
      <b-col>
         <b-list-group> <b-list-group-item button>Friend list</b-list-group-item>
     
       <table style="width:100%">
  <tr>
    <th>id</th>
    <th>name</th>
    <th>Age</th>
  </tr>
  <tr v-for="user in users" :key="user.id" >
    <th>{{users.id}}</th>
    <th>{{users.name}}</th>
    <th>{{users.email}}</th>
  </tr>
 
</table>
  
  
        </b-list-group>
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  export default {
    name: 'List',
    data () {
      return {
       users:[
         {id:1,name:'adarsh',email:'adarsg@fnasa.com'},
         {id:2,name:'xyz',email:'adarsg@fnasa.com'},
         {id:3,name:'asdf',email:'adarsg@fnasa.com'},
         {id:4,name:'qwer',email:'adarsg@fnasa.com'},
         {id:5,name:',mnb',email:'adarsg@fnasa.com'},
         {id:6,name:'kjhgfyh',email:'adarsg@fnasa.com'}
         ]
       

      }
    },
   

    
  }
</script>
<style >
ul li{
  list-style: none;
}
#list :hover{
 
  cursor: pointer;
}


</style>