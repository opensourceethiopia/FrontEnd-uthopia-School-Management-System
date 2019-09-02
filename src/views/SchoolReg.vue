<template>
  <div class="schoolReg">
    <v-card class="mx-auto" width="90%">
      <v-card-text>
        <h1>School Registration Form</h1>

        <v-form v-model="valid">
          <v-container grid-list-xl light>
            <br />
            <h2>School INFORMATION</h2>

            <v-text-field
            v-model="Sname"
            :counter="100"
            label="School Name"
            required
            ></v-text-field>
            <v-text-field
            v-model="Stag"
            :counter="100"
            label="School Tag"
            
            ></v-text-field>
            <v-layout  wrap>
                <v-flex  xs12 md4>
                    <v-btn @click="onpicked">upload the school's logo</v-btn>

                </v-flex>
                
                <v-flex  xs12 md8>
                    <v-card >
                        <v-img  :src="imageurl" height="200"  class="grey darken-4"></v-img>
                    </v-card>

                </v-flex>
            </v-layout>
           
            
            <input
            type="file"
            ref="fileinput"
            @change="onpickedfiles"
            accept="image/*"
            style="display: none"
            />


            <h2>School Address</h2>

            <v-text-field label="Phone Number" v-model="PhoneNo" type='number'></v-text-field>
            <v-text-field label="P.O.B Number" v-model="POB" type='number'></v-text-field>

            <h2>Grade</h2>
            <h2>Section</h2>
            <h2>Subject</h2>

            <v-container v-for="(Subject,index) in Subjects" :key="index">
                <v-text-field
                v-model="Subject.name"
                :counter="100"
                label="Subject Name"
                required
                ></v-text-field>
                <v-select :items='Grades' label="Grade" v-model="Subject.Grade"></v-select>
                <v-select :items='Sections' label="Section" v-model="Subject.Section"></v-select>
                <v-btn small color="error" @click="removeS(index)">Remove Subject</v-btn>

            </v-container>

            <v-btn small color="primary" @click="addS">Add Subject</v-btn>

          </v-container>
        </v-form>
      </v-card-text>
    </v-card>

    
    </div>
</template>

<script lang="ts">
import Vue from "vue"
import axios from 'axios'
import VueAxios from 'vue-axios'
 
Vue.use(VueAxios, axios)

export default Vue.extend({
  data() {
    return {
        Sname: '',
        Stag: '',
        imageurl: '',
        logo: '',
        PhoneNo: '',
        POB: '',
        Subjects: [{
            name:'',
            Grade:'',
            Section:''

        }],
        Grades: ['1'],
        Sections:['w'],

      
      }
 
    },
    methods:{
        addS() {
        this.Subjects.push({
            name: "",
            Grade: "",
            Section: "",
            
            });
        },
        removeS(index) {
        this.Subjects.splice(index, 1);
        },
        onpicked() {
            this.$refs.fileinput.click();
        },
        onpickedfiles(event) {
            const file = event.target.files;

            var filereader = new FileReader();

            filereader.onload = e => {
                this.imageurl = filereader.result as string;
            };
            filereader.readAsDataURL(file[0]);
            this.logo = file[0];
        }
      
    },

});
</script>
