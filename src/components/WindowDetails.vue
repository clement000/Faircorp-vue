<template>
    <div>
        <div>
            <h4>{{ window.name }}</h4>
            <li>room : <span>{{ window.room.name }}</span></li>
            <li>current room temperature : <span>{{ window.room.currentTemperature }}</span></li>
            <li>target room temperature : <span>{{ window.room.targetTemperature }}</span></li>
            <li>Status : <span>{{window.windowStatus}}</span></li>
        </div>
        <h5>
            There is no additional information on this page, 
            but we could add more details on windows, 
            or even add options to open/close them.
        </h5>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
      return {
          window: []
      }
  },
  async created() {
    const apiUrl = "http://127.0.0.1:8080/api/"
    const id = this.$route.params.id
    const response = await axios.get(apiUrl + "windows/" + id);
    this.window = replaceNull(response.data);
    console.log(this.window);
    console.log("test");
  }
}

function replaceNull(window) {
    if (window.room.targetTemperature == null) {
        window.room.targetTemperature = "NO DATA";
    }
    else{
        window.room.targetTemperature += " °C"
    }
    if (window.room.currentTemperature == null) {
        window.room.currentTemperature = "NO DATA";
    }
    else{
        window.room.currentTemperature += " °C"
    }
    return window;
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
