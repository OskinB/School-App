<template>
  <div class="page-holder">
    <section class="page-title">
      <div class="main-title">
        <img src="../assets/waitinglist-img.svg" alt="Biðlisti" />
        <h1>Biðlisti</h1>
      </div>
      <div class="total-waiting-time" id="waitingListTime-display" v-if="showCard === false">
        <h2>{{ waitTime }} mín bið</h2>
      </div>
    </section>

    <SelectTeacher v-if="showCard === true" @click.native="showNext" />
    <AllWaitingList
      v-if="showList"
      @get-total-time="showTotalTime"
      @back-to-select="showCardAgain"
      v-bind="$props"
    />
  </div>
</template>

<script>
import SelectTeacher from "@/components/sections/SelectTeacher";
import AllWaitingList from "@/components/sections/AllWaitingList";

export default {
  props: {
    logedUserInfo: Object
  },
  components: {
    SelectTeacher,
    AllWaitingList
  },
  data() {
    return {
      showList: false,
      showCard: true,
      waitTime: 10
    };
  },
  methods: {
    showNext() {
      this.showList = true;
      this.showCard = false;
    },
    showTotalTime(time) {
      this.waitTime = time;
    },
    showCardAgain() {
      this.showCard = true;
      this.showList = false;
    }
  }
};
</script>


<style lang="scss">
.page-title {
  @include flex(row, space-between, center);
  color: $navy-blue;
  margin: 32px 0 48px;

  .main-title {
    @include flex(row, flex-start, center);
    h1 {
      font-size: 32px;
      font-weight: 500;
      margin-left: 8px;
    }
  }
  .total-waiting-time {
    h2 {
      font-size: 16px;
      line-height: 32px;
      font-weight: bold;
    }
  }
}

// *** DESKTOP SIZE ***
@media only screen and (min-width: 900px) {
  .page-title {
    .total-waiting-time {
      margin-right: 40px;
      h2 {
        font-size: 32px;
        line-height: 46px;
      }
    }
  }
}
</style>
