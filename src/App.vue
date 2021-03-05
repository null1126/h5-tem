<template>
  <router-view />
  <van-button size="mini" color="linear-gradient(to right, #ff6034, #ee0a24)">渐变色按钮</van-button>

  <van-button plain hairline size="mini" type="primary">细边框按钮</van-button>

  <van-button round size="mini" type="primary">圆形按钮</van-button>

  <van-cell title="选择日期区间" :value="date" @click="show = true" />

  <van-calendar v-model:show="show" type="range" @confirm="onConfirm" />

</template>

<script>
import { Button, Cell, Calendar } from 'vant'
import { ref } from 'vue';
export default {
  components: {
    vanButton: Button,
    vanCell: Cell,
    vanCalendar: Calendar,
  },
  setup() {
    const date = ref('');
    const show = ref(false);

    const formatDate = (date) => `${date.getMonth() + 1}/${date.getDate()}`;
    const onConfirm = (values) => {
      const [start, end] = values;
      show.value = false;
      date.value = `${formatDate(start)} - ${formatDate(end)}`;
    };

    return {
      date,
      show,
      onConfirm,
    };
  },
}
</script>

<style lang="less">
*{
  box-sizing: border-box;
}
</style>
