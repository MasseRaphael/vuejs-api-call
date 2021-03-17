<template>
    <Layout>
        <article v-for="event in agendaEvents" :key="event.uid">
            <h1>{{ event.title.fr }}</h1>
            <img
            v-if="event.image"
             :src="event.image.base + events.image.filemane"/>
            <p>
                Date : {{ event.dateRange.fr }}
            </p>
            <address>
                {{ event.location.name }}<br>
                {{ event.location.address }}
            </address>
        </article>
    </Layout>
</template>
<script>
export default{
    data(){
        return {
            agenda: ''
        }
    },
    async mounted() {
        const result = await fetch(`https://${process.env.GRIDSOME_AGENDA_URL}/agendas/${process.env.GRIDSOME_AGENDA_UID}/events.v2.json?key=${process.env.GRIDSOME_AGENDA_KEY}`)
        .then(response =>{
            return response.json()
        })
        .then(json => {
            return json
        })
        this.agenda = result
    },
    computed: {
        agendaEvents(){
            return this.agenda.events
        }
    }
}

</script>
