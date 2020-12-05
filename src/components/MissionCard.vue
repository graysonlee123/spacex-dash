<template>
  <div class="card">
    <p class="faint">Mission Details</p>
    <p>
      {{ mission.details || "No details provided" }}
    </p>
    <table>
      <tr v-if="mission.flight_number">
        <td class="faint">
          Flight Number
        </td>
        <td>
          {{ mission.flight_number }}
        </td>
      </tr>
      <tr v-if="mission.launch_date_utc">
        <td class="faint">
          Launch Date
        </td>
        <td>
          {{ mission.launch_date_utc }}
        </td>
      </tr>
      <tr v-if="mission.last_date_update">
        <td class="faint">
          Last Updated
        </td>
        <td>
          {{ dateForHumans(mission.last_date_update) }}
        </td>
      </tr>
      <tr>
        <td class="faint">
          Launch Site
        </td>
        <td>
          {{ mission.launch_site.site_name_long || "Not Provided" }}
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import dayjs from "dayjs";

export default {
  name: "MissionCard",
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

<style lang="scss" scoped>
.card {
  margin-bottom: 2rem;
  width: 472px;
  margin-left: auto;
  margin-right: auto;
  padding: 3rem 2rem;
  background-color: #eee;
  border-radius: 1rem;
  box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.2);
}

.faint {
  opacity: 0.25;
  font-weight: bold;
  font-size: 0.75rem;
  text-transform: uppercase;
  padding-right: 1rem;
}
</style>
