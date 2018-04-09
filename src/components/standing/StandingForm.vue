<style lang="scss" scoped>
table {
  border-collapse: collapse;
  border: solid 2px;
}
table th, table td {
  border: solid 1px;
}
</style>

<template>
  <div>

  <center>
  <table border="1" align="center">
    <tr>
      <th>チーム名</th>
      <th>試合数</th>
      <th>勝ち</th>
      <th>引き分け</th>
      <th>負け</th>
      <th>勝点</th>
    </tr>
    <tr v-for="result in results" v-bind:key="result.team_id" align="center">
      <td style="height:100px; width:100px"> {{ result.team_name }} </td>
      <td style="height:100px; width:100px"> {{ result.overall_gp }} </td>
      <td style="height:100px; width:100px"> {{ result.overall_w }} </td>
      <td style="height:100px; width:100px"> {{ result.overall_d }} </td>
      <td style="height:100px; width:100px"> {{ result.overall_l }} </td>
      <td style="height:100px; width:100px"> {{ result.points }} </td>
    </tr>
  </table>
  </center>

  <br>

  <center>
  <table border="1">
    <tr>
      <th style="height:100px; width:100px">asdf</th>
      <th style="height:100px; width:100px">sdf</th>
    </tr>
    <tr>
      <td>987</td>
      <td>87</td>
    </tr>
  </table>
  </center>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'standing-form',
  data() {
    return {
      results: {},
    };
  },
  mounted() {
    const apiURL = 'http://api.football-api.com/2.0/standings/1204?Authorization=565ec012251f932ea4000001fa542ae9d994470e73fdb314a8a56d76';
    axios.get(apiURL).then((res) => {
      this.results = res.data;
      console.log(res);
    })
    .catch(err => console.log(err));
  },
};
</script>
