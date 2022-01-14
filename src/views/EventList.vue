<template>
  <div class="events">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>Up Coming Events</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
// import axios from "axios";
import EventServices from '../services/EventServices.js'
export default {
  name: 'EventList',
  components: {
    EventCard,
  },

  data() {
    return {
      // events:null,
      events: [],
    }
  },

  created() {
    EventServices.getEvents()
      // axios
      //   .get(
      //     "https://my-json-server.typicode.com/Sampad-Sarker/apiDatabase/events"
      //   )
      .then((res) => {
        console.log(res)
        this.events = res.data
      })
      .catch((err) => {
        console.log(err)
      })
  },
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
