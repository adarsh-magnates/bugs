<template>
  <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col></b-col>
   <b-col>
 <div class="hello">
    <b-card-text>
      <h3>Form</h3>
     
    </b-card-text>
     <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
  
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          
        ></b-form-input>
         
       <span>{{errorEmail[0]}}</span>
      </b-form-group>
     

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          placeholder="Enter name"
         
        ></b-form-input>
      </b-form-group>
       <span>{{errorName[0]}}</span>

    <b-form @submit.stop.prevent>
    <label for="text-password">Password</label>
    <b-form-input type="password" id="text-password" aria-describedby="password-help-block"  v-model="form.password"  placeholder="Enter Password"></b-form-input>
    <b-form-text id="password-help-block">
      <!-- Your password must be 8-20 characters long, contain letters and numbers. -->
        <span>{{errorPassword[0]}}</span>
    </b-form-text>
   </b-form>

      <b-form-group id="input-group-4" v-slot="{ ariaDescribedby }">
        <b-form-checkbox-group
          v-model="form.checked"
          id="checkboxes-4"
          :aria-describedby="ariaDescribedby"
        >
          <b-form-checkbox value="me">Terms and condtions</b-form-checkbox>
          <!-- <b-form-checkbox value="that">Check that out</b-form-checkbox> -->
           <span>{{errorChecked[0]}}</span>
        </b-form-checkbox-group>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <!-- <span v-if="error.length">
       <ul>
         <li id="msg" v-for="msg in error" :key="msg.id">
                {{msg}}
         </li>
       </ul> 
       
       </span>   -->
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
  </div>
  </div>




   </b-col>

            
        <b-col></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  export default {
    name: 'Form',
     data() {
      return {
        form: {
          email: '',
          name: '',
          password: null,
          checked: []
        },
  
     errorEmail:[],
      errorName:[],
       errorPassword:[],
        errorChecked:[],
        show: true
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
      //  console.log(this.form.email)
       // alert(JSON.stringify(this.form));
      

        this.error=[];
         if(!this.form.email){
              this.errorEmail.push("**please enter your email");
       }
       
        if(!this.form.name){
           this.errorName.push("**please enter your name");
       }
     
       if(!this.form.password){     
                this.errorPassword.push("**please enter your password");
       }  if(this.form.checked==0){
                this.errorChecked.push("**please check the terns and condition");
       }
    
      //console.warn("error"+this.error)
       
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.name = ''
        this.form.password = null
        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }

     
    },
   // mounted(){
  //  this.errorEmail.length==0;
  //  this.errorName.length==0;
  //  this.errorPassword.length==0;
  //  this.errorChecked.length==0;
  //  console.log(this.errorChecked.length)
    // }
  
  
  }
</script>

<style >
span{
  text-align: center;
  font-size: 12px;
  font-style: italic;
  text-decoration: none;
  list-style-type: none;
  color:red;
}
</style>