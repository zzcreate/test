<template>
  <div class="goods-item" @click="itemClick">
    <img :src="showImage" alt="" />
    <div class="goods-info">
      <p>{{ goodsItem.title }}</p>
      <span class="price">{{ goodsItem.price }}</span>
      <span class="collect">{{ goodsItem.cfav }}</span>
    </div>
  </div>
</template> 
<script>
export default {
  name: "GoodsListItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  computed: {
    showImage() {
      return this.goodsItem.image || this.goodsItem.show.img;
    },
  },
  methods: {
    itemClick() {
      if (this.goodsItem.iid) {
        this.$router.push("/detail/" + this.goodsItem.iid).catch((err) => err);
      }
    },
  },
};
</script>

<style scoped>
.goods-item {
  position: relative;
  width: 48%;
  padding-bottom: 40px;
}
.goods-item img {
  width: 100%;
  border-radius: 5px;
}
.goods-info {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 5px;
  font-size: 12px;
  text-align: center;
}
.goods-info p {
  overflow: hidden;
  margin-bottom: 3px;
  white-space: nowrap;
  text-overflow: ellipsis;
}
.price {
  margin-right: 20px;
  color: var(--color-high-text);
}
.collect {
  position: relative;
}
.collect::before {
  position: absolute;
  left: -15px;
  top: -1px;
  content: "";
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
}
</style>