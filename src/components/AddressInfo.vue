<template>
  <div class="info">
    <div class="info__input">
      <span class="info__input__title">所在城市：</span>
      <input
        type="text"
        class="info__input__content"
        placeholder="如北京市"
        v-model="createData.city"
      />
    </div>
    <div class="info__input">
      <span class="info__input__title">小区/大厦/学校：</span>
      <input
        type="text"
        class="info__input__content"
        placeholder="如理工大学国防科技园"
        v-model="createData.department"
      />
    </div>
    <div class="info__input">
      <span class="info__input__title">楼号-门牌号：</span>
      <input
        type="text"
        class="info__input__content"
        placeholder="A号楼B层"
        v-model="createData.houseNumber"
      />
    </div>
    <div class="info__input">
      <span class="info__input__title">收货人：</span>
      <input
        type="text"
        class="info__input__content"
        placeholder="请填写收货人的姓名"
        v-model="createData.name"
      />
    </div>
    <div class="info__input">
      <span class="info__input__title">联系电话：</span>
      <input
        type="text"
        class="info__input__content"
        placeholder="请填写收货手机号"
        v-model="createData.phone"
      />
    </div>
  </div>
</template>

<script>
import { reactive, watch } from 'vue'

export default {
  name: 'AddressInfo',
  props: ['infoData'],
  setup(props, context) {
    const createData = reactive({
      city: '',
      department: '',
      houseNumber: '',
      name: '',
      phone: '',
    })

    watch(
      () => props.infoData,
      (newvalue, oldvalue) => {
        createData.city = props.infoData.city
        createData.department = props.infoData.department
        createData.houseNumber = props.infoData.houseNumber
        createData.name = props.infoData.name
        createData.phone = props.infoData.phone
      },
      { deep: true, immediate: true }
    )

    return { createData }
  },
}
</script>

<style lang="scss" scoped>
@import '../style/viriables.scss';
.info {
  margin: 0.12rem;
  &__input {
    line-height: 0.45rem;
    font-size: 0.14rem;
    color: $medium-fontcolor;
    background-color: $bgColor;
    padding: 0 0.18rem;
    border-bottom: 0.01rem solid $content-bgColor;
    &__content {
      width: 60%;
      outline: none;
      border: none;
      ::placeholder {
        color: $light-fontcolor;
      }
    }
  }
}
</style>
