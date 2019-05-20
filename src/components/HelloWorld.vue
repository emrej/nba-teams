<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-1"></div>
        <div class="col-10">
          <FilterDropdown v-bind:states="getStates"
                          v-bind:conferences="getConferences"
                          v-bind:divisions="getDivisions"
                          v-on:filterTeamsPerConference="filterTeamsPerConference"
                          v-on:filterTeamsPerState="filterTeamsPerState"
                          v-on:filterTeamsPerDivision="filterTeamsPerDivision"
                          v-on:cancelFilter="cancelFilter"></FilterDropdown>
        </div>
        <div class="col-1"></div>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-4 mb-2" v-for="team in filteredTeams" v-bind:key="team.name">
          <b-card :img-src="team.image"
                  img-alt="Image"
                  img-top
                  tag="article"
                  style="max-width: 20rem;"
                  class="h-80">
            <h3 slot="header" class="mb-0">{{team.name}}</h3>
            <b-card-text>
              {{team.city}}, {{team.state}}
            </b-card-text>
            <b-card-text>
              {{team.conference}} - {{team.division}}
            </b-card-text>
            <b-card-text>
              {{team.stadium}}
            </b-card-text>
            <b-button href="#" variant="primary">Go somewhere</b-button>
          </b-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FilterDropdown from "./FilterDropdown";
import uniq from 'lodash/uniq';
export default {
  name: 'HelloWorld',
    components: {FilterDropdown},
    props: {
        msg: String,
  },
    created(){
        this.filteredTeams = this.teams;
    },
    methods:{
      filterTeamsPerState(state){
        if(state !==''){
            this.filteredTeams = this.teams.filter(team => team.state === state);
        }
      },
        filterTeamsPerConference(conference){
          if(conference !=='')
            this.filteredTeams = this.teams.filter(team => team.conference === conference);
        },
        filterTeamsPerDivision(division){
            if(division !=='')
                this.filteredTeams = this.teams.filter(team => team.division === division);
        },
        cancelFilter(){
          this.filteredTeams = this.teams;
        }
    },
    data(){
      return {
          filteredTeams: [],
          teams: [
              {
                  conference: "Eastern",
                  division: "Atlantic",
                  name: "Boston Celtics",
                  city: "Boston",
                  state: "MA",
                  stadium: "TD Garden",
                  image: "../assets/boston.png"
              },
              {
                  conference: "Eastern",
                  division: "Atlantic",
                  name: "Brooklyn Nets",
                  city: "New York",
                  state: "NY",
                  stadium: "Barclays Center",
                  image: "../assets/brooklyn.png"
              },
              {
                  conference: "Eastern",
                  division: "Atlantic",
                  name: "New York Knicks",
                  city: "New York",
                  state: "NY",
                  stadium: "Madison Square Garden",
                  image: "../assets/knicks.png"
              },
              {
                  conference: "Eastern",
                  division: "Atlantic",
                  name: "Philadelphia 76ers",
                  city: "Philadelphia",
                  state: "PA",
                  stadium: "Wells Fargo Center",
                  image: "../assets/76ers.png"
              },
              {
                  conference: "Eastern",
                  division: "Atlantic",
                  name: "Toronto Raptors",
                  city: "Toronto",
                  state: "ON",
                  stadium: "Air Canada Centre",
                  image: "../assets/raptors.png"
              },
              {
                  conference: "Eastern",
                  division: "Central",
                  name: "Chicago Bulls",
                  city: "Chicago",
                  state: "IL",
                  stadium: "United Center",
                  image: "../assets/bulls.png"
              },
              {
                  conference: "Eastern",
                  division: "Central",
                  name: "Cleveland Cavaliers",
                  city: "Cleveland",
                  state: "OH",
                  stadium: "Quicken Loans Arena",
                  image: "../assets/cavaliers.png"
              },
              {
                  conference: "Eastern",
                  division: "Central",
                  name: "Detroit Pistons",
                  city: "Auburn Hills",
                  state: "MI",
                  stadium: "The Palace of Auburn Hills",
                  image: "../assets/pistons.png"
              },
              {
                  conference: "Eastern",
                  division: "Central",
                  name: "Indiana Pacers",
                  city: "Indianapolis",
                  state: "IN",
                  stadium: "Bankers Life Fieldhouse",
                  image: "../assets/pacers.png"
              },
              {
                  conference: "Eastern",
                  division: "Central",
                  name: "Milwaukee Bucks",
                  city: "Milwaukee",
                  state: "WI",
                  stadium: "BMO Harris Bradley Center",
                  image: "../assets/bucks.png"
              },
              {
                  conference: "Eastern",
                  division: "Southeast",
                  name: "Atlanta Hawks",
                  city: "Atlanta",
                  state: "GA",
                  stadium: "Philips Arena",
                  image: "../assets/hawks.png"
              },
              {
                  conference: "Eastern",
                  division: "Southeast",
                  name: "Charlotte Hornets",
                  city: "Charlotte",
                  state: "NC",
                  stadium: "Spectrum Center",
                  image: "../assets/hornets.png"
              },
              {
                  conference: "Eastern",
                  division: "Southeast",
                  name: "Miami Heat",
                  city: "Miami",
                  state: "FL",
                  stadium: "American Airlines Arena",
                  image: "../assets/heat.png"
              },
              {
                  conference: "Eastern",
                  division: "Southeast",
                  name: "Orlando Magic",
                  city: "Orlando",
                  state: "FL",
                  stadium: "Amway Center",
                  image: "../assets/magic.png"
              },
              {
                  conference: "Eastern",
                  division: "Southeast",
                  name: "Washington Wizards",
                  city: "Washington, D.C.",
                  stadium: "Verizon Center",
                  image: "../assets/wizards.png"
              },
              {
                  conference: "Western",
                  division: "Northwest",
                  name: "Denver Nuggets",
                  city: "Denver",
                  state: "CO",
                  stadium: "Pepsi Center",
                  image: "../assets/nuggets.png"
              },
              {
                  conference: "Western",
                  division: "Northwest",
                  name: "Minnesota Timberwolves",
                  city: "Minneapolis",
                  state: "MN",
                  stadium: "Target Center",
                  image: "../assets/timberwolves.png"
              },
              {
                  conference: "Western",
                  division: "Northwest",
                  name: "Oklahoma City Thunder",
                  city: "Oklahoma city",
                  state: "OK",
                  stadium: "Chesapeake Energy Arena",
                  image: "../assets/oklahoma.png"
              },
              {
                  conference: "Western",
                  division: "Northwest",
                  name: "Portland Trail Blazers",
                  city: "Portland",
                  state: "OR",
                  stadium: "Moda Center",
                  image: "../assets/blazers.png"
              },
              {
                  conference: "Western",
                  division: "Northwest",
                  name: "Utah Jazz",
                  city: "Salt Lake city",
                  state: "UT",
                  stadium: "Vivint Smart Home Arena",
                  image: "../assets/jazz.png"
              },
              {
                  conference: "Western",
                  division: "Pacific",
                  name: "Golden State Warriors",
                  city: "Oakland",
                  state: "CA",
                  stadium: "Oracle Arena",
                  image: "../assets/warriors.png"
              },
              {
                  conference: "Western",
                  division: "Pacific",
                  name: "Los Angeles Clippers",
                  city: "Los Angeles",
                  state: "CA",
                  stadium: "Staples Center",
                  image: "../assets/clippers.png"
              },
              {
                  conference: "Western",
                  division: "Pacific",
                  name: "Los Angeles Lakers",
                  city: "Los Angeles",
                  state: "CA",
                  stadium: "Staples Center",
                  image: "../assets/lakers.png"
              },
              {
                  conference: "Western",
                  division: "Pacific",
                  name: "Phoenix Suns",
                  city: "Phoenix",
                  state: "AZ",
                  stadium: "Talking Stick Resort Arena",
                  image: "../assets/suns.png"
              },
              {
                  conference: "Western",
                  division: "Pacific",
                  name: "Sacramento Kings",
                  city: "Sacramento",
                  state: "CA",
                  stadium: "Golden 1 Center",
                  image: "../assets/kings.png"
              },
              {
                  conference: "Western",
                  division: "Southwest",
                  name: "Dallas Mavericks",
                  city: "Dallas",
                  state: "TX",
                  stadium: "American Airlines Center",
                  image: "../assets/mavericks.png"
              },
              {
                  conference: "Western",
                  division: "Southwest",
                  name: "Houston Rockets",
                  city: "Houston",
                  state: "TX",
                  stadium: "Toyota Center",
                  image: "../assets/rockets.png"
              },
              {
                  conference: "Western",
                  division: "Southwest",
                  name: "Memphis Grizzlies",
                  city: "Memphis",
                  state: "TN",
                  stadium: "FedExForum",
                  image: "../assets/grizzelies.png"
              },
              {
                  conference: "Western",
                  division: "Southwest",
                  name: "New Orleans Pelicans",
                  city: "New Orleans",
                  state: "LA",
                  stadium: "Smoothie King Center",
                  image: "../assets/pelicans.png"
              },
              {
                  conference: "Western",
                  division: "Southwest",
                  name: "San Antonio Spurs",
                  city: "San Antonio",
                  state: "TX",
                  stadium: "AT&T Center",
                  image: "../assets/spurs.png"
              }
          ]
      };
    },
    computed:{
      getStates() {
          return uniq(this.teams.map(team => team.state));
      },
      getConferences(){
        return uniq(this.teams.map(team => team.conference));
      },
        getDivisions(){
            return uniq(this.teams.map(team => team.division));
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
:host{
  @import "";
}
</style>
