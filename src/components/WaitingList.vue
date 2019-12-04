<template>
  <div class="page-holder">
    <section class="page-title">
      <div class="main-title">
        <img src="../assets/waitinglist-img.svg" alt="Biðlisti" />
        <h1>Biðlisti</h1>
      </div>
      <div class="total-waiting-time" id="waitingListTime-display">
        <h2>10 mín bið</h2>
      </div>
    </section>
    <SelectTeacher />
  </div>
</template>

<script>
import SelectTeacher from "@/components/sections/Student-selectTeacher";
import AllWaitingList from "@/components/sections/AllWaitingList";

export default {
  components: {
    SelectTeacher,
    AllWaitingList
  }
};
</script>


<style lang="scss" scope>
.page-title {
  @include flex(row, space-between, center);
  color: $navy-blue;
  margin: 32px 0 48px;

  .main-title {
    @include flex(row, flex-start, center);
    h1 {
      font-size: 32px;
      // *Vantar: font-weight: 500/medium;
      margin-left: 8px;
    }
  }
  .total-waiting-time {
    h2 {
      font-size: 24px;
      line-height: 32px;
      font-weight: bold;
    }
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  .total-waiting-time {
    margin-right: 40px;
    h2 {
      font-size: 32px;
      line-height: 46px;
    }
  }
}
</style>
