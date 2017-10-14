<template>
  <div class="hello">
<h1>จองห้องพัก TaveechaiVilla</h1>
<form v-on:submit.prevent='addbook'>
  Status: <select v-model="status">
<option value="ckeck_in" v-model="title">check in</option>
<option value="check_out">check out</option>
</select><br>
Name :
<input :value="Name" type="text" v-model="name"><br>
Surename :
<input :value="Surename" type="text" v-model="surename"><br>
RoomNumber :
<input :value="room" type="text" v-model="room"><br>
Time :
<input :value="Surename" type="text" v-model="time"><br>
Day : <input :value="day" type="text" v-model="day"><br>
<input type='submit' class='add'  value= "addbook">
<br>
  </form>
</div>
</template>
<script>
import Firebase from 'firebase'
let config = {
  apiKey: 'AIzaSyC-RGOcNEEPtEmatuomhy1rhMVqq8cfEo4',
  authDomain: 'vuejs-firebase-02-7c441.firebaseapp.com',
  databaseURL: 'https://vuejs-firebase-02-7c441.firebaseio.com',
  projectId: 'vuejs-firebase-02-7c441',
  storageBucket: 'vuejs-firebase-02-7c441.appspot.com',
  messagingSenderId: '314142710279'
}
let app = Firebase.initializeApp(config)
let db = app.database()
let villaref = db.ref('villa')
export default {
  name: 'HelloWorld',
  firebase: {
    villa: villaref
  },
  data () {
    return {
      newroom: {
        room: '',
        surename: '',
        name: '',
        day: '',
        status: '',
        time: ''
      }
    }
  },
  methods: {
    addbook: function () {
      villaref.push({
        room: this.room,
        surename: this.surename,
        name: this.name,
        day: this.day,
        status: this.status,
        time: this.time
      })
      this.newroom.room = ''
      this.newroom.surename = ''
      this.newroom.name = ''
      this.newroom.day = ''
      this.newroom.status = ''
      this.newroom.time = ''
    }
  }
}
</script>
<style>
button { width: 50px;
height: 30px;}
</style>
