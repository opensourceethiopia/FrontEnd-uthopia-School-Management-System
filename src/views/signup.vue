<template>
  <div class="signup" >
    
    <v-card class="mx-auto" width="90%"> 
        <v-card-text>

        
        <h1>Registration Form</h1>
        

        <v-form v-model="valid">
        <v-container grid-list-xl light>

          <br>
          <h2>PERSONAL INFORMATION</h2> 
          
          <v-layout wrap>
            
              
            <v-flex
              xs12
              md4
            >
              
              <v-text-field
                v-model="firstname"
                :rules="nameRules"
                :counter="20"
                label="First name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex
              xs12
              md4
            >
              <v-text-field
                v-model="Middlename"
                :rules="nameRules"
                :counter="20"
                label="Middle name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex
              xs12
              md4
            >
              <v-text-field
                v-model="lastname"
                :rules="nameRules"
                :counter="20"
                label="Last name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex 
              xs12
              md5>
              <v-menu
              ref="menu"
              v-model="menu"
              :close-on-content-click="false"
              transition="scale-transition"
              offset-y
              full-width
              max-width="290px"
              >
              <template v-slot:activator="{ on }">
                <v-text-field
                  v-model="date"
                  label="Birthday date"
                  prepend-inner-icon=""
                  readonly
                  v-on="on"
                  
                ></v-text-field>
              </template>
              <v-date-picker v-model="date" no-title scrollable>
                <div class="flex-grow-1"></div>
                <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
              </v-date-picker>
            </v-menu>
            </v-flex>

            <v-flex xs12 md6>
              <v-text-field v-model="id" label="ID" disabled="true">
              </v-text-field>
              
            </v-flex>


            <v-flex
              xs12
              md8
              lg8 class="mx-auto">
              
              
               <v-card>
                <v-img
                  v-if="imageDesplay"
                  :src="imageurl"
                  height="300"
                  class="grey darken-4"
                ></v-img>
                
              </v-card>
              
            </v-flex>
            <input type="file" ref="fileinput" @change="onpickedfiles" accept="image/*" style="display: none">

            <v-flex
              xs12
              md6
            >

              <!-- <v-file-input
                v-model="image"
                accept="image/*"
                :placeholder="placehold"
                prepend-icon="mdi-camera"
                label="profile picture"
                @click="onpicked"
              ></v-file-input>
             -->

            <v-btn @click="onpicked" >upload a picture</v-btn>
          </v-flex>
            

            <v-flex
              xs12
              md6>
              <v-select
                v-model="sex"
                :items="['male','female']"
                label="Gender"
                solo
                
              ></v-select>
            </v-flex>
         
            
        </v-layout>
        <h2>STATUS</h2>
        <v-layout wrap>
           
            <v-flex xs12
              md6>
              <v-select :items="items" v-model='Grade' label="Grade">

              </v-select>

            </v-flex>
            

            <v-flex
              xs12
              md6
            >
            <v-text-field label="Section" v-model='Section' disabled='true'></v-text-field>
              
            </v-flex>

            <v-flex
              xs12
              md6
            >
            <v-text-field label="Year Of Entered" v-model='EnteredYear'>{{EnteredYear}}</v-text-field>
              
            </v-flex>

    
        </v-layout>

        <h2>Guardian Information</h2>

        
            
           
          <v-container v-for='(parentInfo,index) in ParentInfo' :key="index">
            <v-layout wrap>
              <v-flex
              xs12
              md4
            >
              
              <v-text-field
                v-model="parentInfo.FirstName"
                :rules="nameRules"
                :counter="20"
                label="First name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex
              xs12
              md4
            >
              <v-text-field
                v-model="parentInfo.MiddleName"
                :rules="nameRules"
                :counter="20"
                label="Middle name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex
              xs12
              md4
            >
              <v-text-field
                v-model="parentInfo.LastName"
                :rules="nameRules"
                :counter="20"
                label="Last name"
                required
              ></v-text-field>
            </v-flex>

            <v-flex
              xs12
              md6
            >
              <v-select :items='["male","female"]' label="Gender" v-model="parentInfo.Gender"></v-select>
            </v-flex>

            <v-flex
              xs12
              md6
            >
              <v-select :items='relation' label="Relation with the guardian" v-model="parentInfo.Relation"></v-select>
            </v-flex>

            <v-btn small color="error" @click="removeG(index)">Remove Guardian</v-btn>
           
          </v-layout>
        </v-container>
         <br>
        <v-btn small color="primary" @click="addG">Add Guardian</v-btn> 
        <br><br>

        <v-btn class="mr-4" @click="submit">submit</v-btn>
        
        
        </v-container>

        
      </v-form>

            
        
        </v-card-text>
        
    </v-card>
  
    
  </div>
</template>

<script lang="ts">
import Vue from 'vue';




export default Vue.extend({
  
  

  data() {
      return {
        date: null,
        sex: "",
        placehold:"pick a profile picture",
        imageDesplay: false,
        valid: false,
        firstname: '',
        lastname: '',
        Middlename: '',
        imageurl: '',
        image: [],
        id:null,
        Grade:null,
        items: [
        'Grade 1',
        'Grade 2',
        'Grade 3',
        'Grade 4',
        'Grade 5',
        'Grade 6',
        'Grade 7',
        'Grade 8',
        'Grade 9',
        'Grade 10',
        'Grade 11',
        'Grade 12',
        ],
        relation:[
          'mother',
          'father',
          'sister',
          'brother',
          'uncle',
          'aunt'
        ],
        Section:null,
        EnteredYear:new Date().getFullYear(),
        ParentInfo:[{
          FirstName : '',
          MiddleName : '',
          LastName : '' ,
          Gender:'',
          Relation:''
        }],
      
        nameRules: [
            v => !!v || 'Name is required',
            v => v.length <= 20 || 'Name must be less than 10 characters',
        ],
        
        
        
    //
      }
  },
  computed(){
    

  },
  
  methods:{
    addG(){
      this.ParentInfo.push({
          FirstName : '',
          MiddleName : '',
          LastName : '' ,
          Gender:'',
          Relation:''
      })

    },
    removeG(index){
      this.ParentInfo.splice(index,1);
    },
    submit(){
      
      const ID=this.id;
      const Firstname=this.firstname;
      const Lastname=this.lastname;
      const MiddleName=this.Middlename;
      const sex= this.sex;
      const imageF= this.image;
      const DOB=this.date;
      const Grade=this.Grade;
      const Section= this.Section;
      const EnteredYear =this.EnteredYear;
     
      
     

      if(!Firstname || !Lastname || !MiddleName){
        
        
      }


    },
    onpicked(){
     
      this.$refs.fileinput.click();
     
      
      
    },
    // clear(){
      
    //   this.firstname='';
    //   this.lastname='';
    //   this.Middlename='';

    // },
    onpickedfiles(event){
       
      this.imageDesplay =true;
      const file=event.target.files;
      
      
      
      
     
     
      var filereader=new FileReader();
      
      filereader.onload=(e)=>{
       this.imageurl = filereader.result as string
      };
      filereader.readAsDataURL(file[0]);
      this.image=file[0];
      

      



      

    }
  }
});
</script>
