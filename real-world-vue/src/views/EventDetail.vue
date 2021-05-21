<template>
<div v-if="event">
    <h1>{{ event.title }}</h1>
    <h2> {{ event.time }} on {{ event.date }} @ {{ event.location }}</h2>
    <p>{{ event.description }}</p>
</div>
</template>

<script>
import EventService from '@/services/EventService';

export default {
    props: ['id'],
    data() {
        return {
            event: null,
        }
    },

    created() {
        // fetch event (by id) and set local data to returned event. 
        EventService.getEvent(this.id)
        .then(response => {
            this.event = response.data;
            console.log(this.event);
        })
        .catch(error => {
            console.error(error);
        })
    }
}
</script>