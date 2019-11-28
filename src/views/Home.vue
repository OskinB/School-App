<template>
  <div class="container">
    <WaitingList />
    <!-- <Interviews/>
    <DayContent/>-->
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
    width: 100vw;
    margin: 48px 24px;
  }
}
</style>
