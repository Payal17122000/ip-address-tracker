<template>
  <div>
    <h4 class="title"><b>IP Address Tracker</b></h4>
    <form
      id="form"
      class="form-inline form"
      method="post"
      @submit.prevent="onclick"
    >
      <input
        v-model="ip"
        class="form-control mr-lg-6 textbox"
        type="search"
        placeholder="Search for any IP addresses or domain"
      />
      <button
        class="btn btn-dark my-2 my-sm-0 button-image"
        type="submit"
      ></button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      addresses: [],
      ip: '',
      apikey: 'ef3eeb9d020b49d19609313bc88ddb39',
      lat_lng: [62.22875562830978, 99.40894012301204],
    }
  },
  methods: {
    async onclick() {
      // console.log(this.ip)
      //  console.log(this.apikey)
      const res = await this.$axios.$get(
        'https://api.ipgeolocation.io/ipgeo?apiKey=' +
          this.apikey +
          '&ip=' +
          this.ip
      )
      this.addresses = res
      //  console.log(this.addresses)
      this.$router.push('/payal')
    },
  },
}
</script>
