<template>
  <div class="docker">
    <div
      v-for="(item, index) in dockerList"
      :class="{
        docker__item: true,
        'docker__item--active': index === currentIndex,
      }"
      :key="index"
    >
      <router-link :to="item.to">
        <div class="iconfont" v-html="item.icon" />
        <div class="docker__title">{{ item.text }}</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Docker',
  props: ['currentIndex'],
  setup() {
    const dockerList = [
      { icon: '&#xe8b9;', text: '首页', to: { name: 'Home' } },
      { icon: '&#xe742;', text: '购物车', to: { name: 'CartList' } },
      { icon: '&#xe8ae;', text: '订单', to: { name: 'OrderList' } },
      { icon: '&#xe6ef;', text: '我的', to: { name: 'Mine' } },
    ]
    return { dockerList }
  },
}
</script>

<style lang="scss" scoped>
@import '../style/viriables.scss';
.docker {
  display: flex;
  box-sizing: border-box;
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 0.49rem;
  border-top: 0.01rem solid $content-bgColor;
  padding: 0 0.18rem;
  overflow: hidden;
  &__item {
    flex: 1;
    text-align: center;
    a {
      color: $content-fontcolor;
      text-decoration: none;
    }
    .iconfont {
      font-size: 0.18rem;
      margin: 0.07rem 0 0.02rem 0;
    }
    &--active {
      a {
        color: $active-color;
      }
    }
  }
  &__title {
    font-size: 0.2rem;
    transform: scale(0.5, 0.5);
    transform-origin: center top;
  }
}
</style>
