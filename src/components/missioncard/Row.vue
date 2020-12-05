<template>
  <tr>
    <td class="font-bold text-opacity-25 text-xs uppercase pr-4">
      {{ label }}
    </td>
    <td>
      {{ value }}
    </td>
  </tr>
</template>

<script>
export default {
  name: "MissionCardRow",
  props: {
    label: {
      type: String,
      required: true
    },
    value: {
      type: [String, Number],
      required: true
    }
  }
};
</script>
