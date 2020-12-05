<template>
  <div
    class="mb-8 mx-auto py-12 px-8 bg-gray-100 shadow-lg rounded-lg w-96 text-left"
  >
    <p class="font-bold text-opacity-25 text-xs uppercase pr-4">
      Mission Details
    </p>
    <p>
      {{ mission.details || "No details provided" }}
    </p>
    <table>
      <Row label="Flight Number" :value="mission.flight_number" />
      <Row
        label="Launch Date"
        :value="dateForHumans(mission.launch_date_utc)"
      />
      <Row
        label="Last Updated"
        :value="dateForHumans(mission.last_date_update)"
      />
      <Row
        label="Launch Site"
        :value="mission.launch_site.site_name_long || 'Not Provided'"
      />
    </table>
  </div>
</template>

<script>
import dayjs from "dayjs";

import Row from "@/components/missioncard/Row";

export default {
  name: "MissionCard",
  components: {
    Row
  },
  props: {
    mission: {
      type: Object,
      required: true
    }
  },
  methods: {
    dateForHumans: function(date) {
      return dayjs(date).format("MMMM DD, YYYY HH:mma");
    }
  }
};
</script>
