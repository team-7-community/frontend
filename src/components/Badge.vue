<template>
  <div>
    <badge-bronze
      v-if="value < 10"
    />
    <badge-silver
      v-bind="$props"
      v-else-if="value < 40"
    />
    <badge-gold
      v-bind="$props"
      v-else
    />
  </div>
</template>

<script>
import BadgeGold from './BadgeGold.vue';
import BadgeSilver from './BadgeSilver.vue';
import BadgeBronze from './BadgeBronze.vue';

export default {
  props: {
    type: String,
    value: Number,
  },
  components: {
    BadgeGold,
    BadgeSilver,
    BadgeBronze,
  },
};
</script>
