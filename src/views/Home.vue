<template>
  <div class="home">
    <div v-if="!loading && upcomingMissions.length">
      <MissionCard
        v-for="mission in upcomingMissions"
        :key="mission.flight_number"
        :mission="mission"
      />
    </div>
    <button
      @click="
        getUpcomingMissions('https://api.spacexdata.com/v3/launches/upcoming', {
          method: 'GET',
          headers: {
            'Content-Type': 'application/json'
          }
        })
      "
    >
      Get Data
    </button>
  </div>
</template>

<script>
import MissionCard from "@/components/MissionCard";

export default {
  name: "Home",
  components: {
    MissionCard
  },
  data() {
    return {
      loading: true,
      upcomingMissions: []
    };
  },
  methods: {
    getUpcomingMissions: async function(url, options) {
      const response = await fetch(url, options);

      this.upcomingMissions = await response.json();
      this.loading = false;
    }
  }
};
</script>
