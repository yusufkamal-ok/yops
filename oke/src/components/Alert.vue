<template>
<v-card height="200">
    <v-img
          height="400px"
          src="https://www.wallpapertip.com/wmimgs/38-383841_background-random-pic-hd.jpg"
    >
<v-snackbar 
    v-model="alert"
    :color="color"
    top
    timeout="4000"
    multi-line
    text
>
    {{ text }}

<template v-slot:action="{ attrs}">
    <v-btn
    color="red"
    text
    v-bind="attrs"
    @click="close"
    >
    Close
    </v-btn>
    </template>
  </v-snackbar>
    </v-img>
</v-card>
</template>

<script>
import {mapActions, mapGetters} from 'vuex'

export default{
   name: "alert",
   computed : {
       ...mapGetters({
       status: "alert/status",
       color: "alert/color",
       text: "alert/text"
       }),
       alert : {
           get (){
               return this.status;
           },
           set(value){
               this.setAlert({
                   status: value
               });
           }
       }
   },
   methods : {
       ...mapActions({
           setAlert: "alert/set"
       }),
       close(){
           this.setAlert({
               status: false
           });
       }
   }
}
</script>
