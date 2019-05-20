<template>
    <div>
        <b-dropdown id="dropdown-1" :text="'Filter by State : '+ state" class="m-md-2">
            <b-dropdown-item v-for="state in states" v-bind:key="state" v-on:click="filterTeamsPerState(state)">{{state}}</b-dropdown-item>
        </b-dropdown>
        <b-dropdown id="dropdown-1" :text="'Filter by Conference : ' + conference" class="m-md-2">
            <b-dropdown-item v-for="conference in conferences" v-bind:key="conference" v-on:click="filterTeamsPerConference(conference)">{{conference}}</b-dropdown-item>
        </b-dropdown>
        <b-dropdown id="dropdown-1" :text="'Filter by Division : ' + division" class="m-md-2">
            <b-dropdown-item v-for="division in divisions" v-bind:key="division" v-on:click="filterTeamsPerDivision(division)">{{division}}</b-dropdown-item>
        </b-dropdown>
        <b-button variant="outline-secondary" v-on:click="cancelFilter">Cancel filter</b-button>
    </div>
</template>

<script>
    export default {
        name: "FilterDropdown",
        props:{
            states: Array,
            conferences: Array,
            divisions: Array
        },
        methods: {
            filterTeamsPerState(state){
                this.state = state;
                this.$emit('filterTeamsPerState', state);
            },
            filterTeamsPerConference(conference){
                this.conference = conference;
                this.$emit('filterTeamsPerConference', conference);
            },
            filterTeamsPerDivision(division){
                this.division = division;
                this.$emit('filterTeamsPerDivision', division);
            },
            cancelFilter(){
                this.$emit('cancelFilter');
            }
        },
        data(){
            return {
                state: "",
                conference: "",
                division: ""
            };
        }
    }
</script>

<style scoped>

</style>