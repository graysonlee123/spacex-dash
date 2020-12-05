<template>
  <div class="text-center">
    <div v-if="!loading && upcomingMissions.length">
      <MissionCard
        v-for="mission in upcomingMissions"
        :key="mission.flight_number"
        :mission="mission"
      />
    </div>
    <button
      class="py-2 px-4 bg-white font-bold uppercase m-8"
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
import MissionCard from "@/components/missioncard/MissionCard";

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
      this.loading = true;

      const response = await fetch(url, options);

      this.upcomingMissions = await response.json();
      this.loading = false;
    }
  }
};
</script>
