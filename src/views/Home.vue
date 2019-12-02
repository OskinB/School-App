<template>
  <div class="container">
    <WaitingList />
    <!-- <Interviews /> -->
    <!-- <DayContent/> -->
  </div>
</template>

<script>
// @ is an alias to /src
import WaitingList from "@/components/WaitingList.vue";
import Interviews from "@/components/Interviews.vue";
import DayContent from "@/components/DayContent.vue";

export default {
  name: "home",
  components: {
    WaitingList,
    Interviews,
    DayContent
  },
  data() {
    return {
      teacher: false
    };
  },
  computed: {
    testing() {
      console.log("Hæj frá Home.vue");
    }
  },
  mounted() {
    console.log("Hæjjjjaaaaa frá Home.vue");
  }
};
</script>

<style lang="scss" scope>
.container {
  margin: 32px 16px;
}
// Þegar er desktop
@media only screen and (min-width: 900px) {
  .container {
    margin: 48px 32px;
  }
}
</style>
