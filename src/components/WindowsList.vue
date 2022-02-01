<template>
    <div>
        <div v-for="window in windows" :key="window.id" class="window-info" v-on:click="redirectToWindow(window.id)" style="cursor: pointer;">
            <h4>{{ window.name }}</h4>
            <li>room : <span>{{ window.room.name }}</span></li>
            <li>current room temperature : <span>{{ window.room.currentTemperature }}</span></li>
            <li>target room temperature : <span>{{ window.room.targetTemperature }}</span></li>
            <li>Status : <span>{{window.windowStatus}}</span></li>
            
		</div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
      return {
          windows: []
      }
  },
  methods:{
      redirectToWindow(id){
          this.$router.push('/window/' + id); 
      }
  },
  async created() {
    const apiUrl = "http://127.0.0.1:8080/api/"
    const response = await axios.get(apiUrl + "windows");
    this.windows = replaceNull(response.data);
    console.log(this.windows);
    console.log("test");
  }
}

function replaceNull(windows) {
    for (var i=0; i<windows.length; i++) {
        if (windows[i].room.targetTemperature == null) {
            windows[i].room.targetTemperature = "NO DATA";
        }
        else{
            windows[i].room.targetTemperature += " °C"
        }
        if (windows[i].room.currentTemperature == null) {
            windows[i].room.currentTemperature = "NO DATA";
        }
        else{
            windows[i].room.currentTemperature += " °C"
        }
    }
    return windows;
}
</script>

<style scoped>
div.window-info {
    background-color: lightgrey;
    width: 50%;
    margin: 10px;
}
div.window-info li span {
    font-weight: bold;
}
</style>
