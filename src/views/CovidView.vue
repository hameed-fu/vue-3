<template>
  <div class="home">
    <NavBar />
    <h2>Covid information</h2>
    <div class="container">
        <div class="card">
          <div class="card-body">
              <table class="table table-hover table-striped">
                  <tr>
                    <th>Country</th>
                    <th>Total Cases</th>
                    <th>Total Deaths</th>
                    <th>New Cases</th>
                    <th>Total recovered</th>
                    <th>Last Update</th>
                  </tr>

                  <tr v-for="row in result" :key="row.index">
                    <td>{{ row['Country_text'] }}</td>
                    <td>{{ row['Total Cases_text'] }}</td>
                    <td>{{ row['Total Deaths_text'] }}</td>
                    <td>{{ row['New Cases_text'] }}</td>
                    <td>{{ row['Total Recovered_text'] }}</td>
                    <td>{{ row['Last Update'] }}</td>
                  </tr>
                  
              </table>
          </div>
        </div>
    </div>
    
  </div>
</template>
  
  <script>
import NavBar from "../components/NavBar.vue";
import axios from "axios";
 
export default {
  // name: 'CovidView',
  components: {
    NavBar,
  },

  data() {
    return {
      result: null,
    };
  },
  mounted() {
    axios.get("https://covid-19.dataflowkit.com/v1")
      .then((response) => {
        // console.log(response.data)
        this.result = response.data
      })

      .catch((error) => {
        console.log(error)
      })
  },
};
</script>
  