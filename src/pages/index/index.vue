<template>
  <div>
    <div class="region">{{ province }} / {{ city }} / {{ district }}</div>
    <button @click="handleClick" class="click-btn">click me</button>
    <region-selector :isShow="selectorShow" :province="province" :city="city" :district="district" @hideSelector="hideSelector"></region-selector>
  </div>
</template>

<script>
import regionSelector from '@/components/regionSelector';

export default {
  components: {
    regionSelector
  },
  data() {
    return {
      selectorShow: false,
      province: '山东省',
      city: '济南市',
      district: '历下区'
    }
  },
  methods: {
    handleClick() {
      this.selectorShow = true;
    },
    hideSelector(info) {
      console.log(info)
      if (info) {
        [this.province, this.city, this.district] = [info[0].name, info[1].name, info[2].name];
      }
      this.selectorShow = false;
    }
  }
}

</script>

<style  scoped>
.region {
  display: flex;
  justify-content: center;
  height: 50px;
  line-height: 50px;
}
.click-btn {
  width: 200px;
}

</style>
