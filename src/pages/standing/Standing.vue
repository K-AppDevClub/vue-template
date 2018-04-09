<template>
  <ons-page>
    <navbar></navbar>
    <h1> Helloだね </h1>
    <standing-form></standing-form>
    {{ result }}
  </ons-page>
</template>

<script>
import axios from 'axios';
import Navbar from '../../components/navbar/Navbar';
import StandingForm from '../../components/standing/StandingForm';
import EhamaForm from '../../components/form/Form';

export default {
  name: 'standing',
  components: {
    Navbar,
    StandingForm,
    EhamaForm,
  },
  data() {
    return {
      result: {},
    };
  },
  mounted() {
    const apiURL = 'http://192.168.10.200:3000/';
    axios.get(apiURL).then((res) => {
      this.result = res.data.status;
      console.log(res);
    })
    .catch(err => console.log(err));
  },
};
</script>
