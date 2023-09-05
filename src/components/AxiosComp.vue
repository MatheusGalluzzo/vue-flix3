<template>
  <div>
    <div v-if="responseData">
      <h2>Response Data:</h2>
      <pre>{{ responseData }}</pre>
    </div>
    <div v-else>
      <p>Loading...</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      responseData: null
    }
  },
  mounted () {
    this.fetchData()
  },
  methods: {
    fetchData () {
      axios
        .get('http://Localhost:51828/api/v1/movies')
        .then((response) => {
          this.responseData = response.data
        })
        .catch((error) => {
          console.error(error)
        })
    }
  }
}
</script>
