<template>
    <div>
        <div v-for="room in rooms" :key="room.id" class="room-info">
            <h4>{{ room.name }}</h4>
            <li>floor : <span>{{ room.floor }}</span></li>
            <li>current temperature : <span>{{ room.currentTemperature }}</span></li>
            <li>target temperature : <span>{{ room.targetTemperature }}</span></li>
		</div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
      return {
          rooms: []
      }
  },
  async created() {
    const apiUrl = "http://127.0.0.1:8080/api/"
    const response = await axios.get(apiUrl + "room");
    this.rooms = replaceNull(response.data);
    console.log(this.rooms);
    console.log("test");
  }
}

function replaceNull(rooms) {
    for (var i=0; i<rooms.length; i++) {
        if (rooms[i].targetTemperature == null) {
            rooms[i].targetTemperature = "NO DATA";
        }
        else{
            rooms[i].targetTemperature += " °C"
        }
        if (rooms[i].currentTemperature == null) {
            rooms[i].currentTemperature = "NO DATA";
        }
        else{
            rooms[i].currentTemperature += " °C"
        }
    }
    return rooms;
}
</script>

<style scoped>
div.room-info {
    background-color: lightblue;
    width: 50%;
    margin: 10px;
}
div.room-info li span {
    font-weight: bold;
}

</style>
