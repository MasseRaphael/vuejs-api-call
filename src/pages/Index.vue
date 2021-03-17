<template>
    <Layout>
        <pre>{{ agendaResult }}</pre>
        <button v-on:click="apiCall()">Afficher l'agenda</button>
    </Layout>
</template>
<script>
export default{
    data(){
        return {
            AGENDA_URL: "openagenda.com",
            AGENDA_UID: '84339284',
            AGENDA_KEY: 'f510f08cc7ab41feb394928a2123c677',
            agendaResult: ''
        }
    },
    methods: {
        apiCall(){
            fetch(`https://${this.AGENDA_URL}/agendas/${this.AGENDA_UID}/events.v2.json?key=${this.AGENDA_KEY}`)
            .then(response =>{
                return response.json()
            })
            .then(json => {
                this.agendaResult = json
            })
        }
    }
}
</script>
