<template>
  <ul ref="breadcrumb" class="breadcrumb-wrapper">
    <li v-for="(breadCrumb, index) in breadCrumbs" :key="breadCrumb.text">
      <span v-if="index === breadCrumbs.length - 1" class="item-text">
        {{ breadCrumb.text }}
      </span>
      <a
        v-else
        class="item-link"
        :href="
          breadCrumb.path != '' ? `${breadCrumb.path}` : `/`
        "
      >
        {{ breadCrumb.text }}
      </a>
    </li>
  </ul>
</template>
<script>
export default {
  props: {
    breadCrumbs: { type: Array, default: () => [] },
  },
  mounted() {
    // コンポーネントが表示される時一番右側までスクロールさせる
    const breadCrumbList = this.$refs.breadcrumb;
    breadCrumbList.scrollLeft = breadCrumbList.scrollWidth;
  },
};
</script>
<style>
.breadcrumb-wrapper {
  display: flex;
  flex-wrap: nowrap;
  overflow-x: scroll;
  overflow-y: hidden;
  box-sizing: border-box;
  border-width: 1px;
  border-color: #e0e0e0;
  /* IE, Edge スクロールバー非表示 */
  -ms-overflow-style: none;
  /* Firefox スクロールバー非表示 */
  scrollbar-width: none;
}

/* Chrome, Safari スクロールバー非表示 */
.breadcrumb-wrapper::-webkit-scrollbar {
  display: none;
}

.breadcrumb-wrapper li {
  position: relative;
  display: flex;
  align-items: center;
  white-space: nowrap;
  flex-shrink: 0;
}

.breadcrumb-wrapper li:first-of-type .item-link {
  margin-left: 0;
}

.item-link {
  padding-left: 0.75rem;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  font-size: 12px;
  margin-left: 0.75rem;
  margin-right: 0.75rem;
}

.item-text {
  padding-left: 0.75rem;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  font-size: 12px;
  margin-left: 0.75rem;
  margin-right: 0.75rem;
}

.breadcrumb-wrapper li:last-child {
  background-color: #5a5a5a;
  color: #fff;
  flex-grow: 1;
}

.breadcrumb-wrapper li::before {
  top: -1px;
  right: -12px;
  border-width: 18px 0 18px 12px;
  border-color: transparent #e0e0e0 transparent #e0e0e0;
}

.breadcrumb-wrapper li::after {
  top: 0;
  right: -11px;
  border-width: 17px 0 17px 12px;
  border-color: transparent transparent transparent #fff;
}

.breadcrumb-wrapper li:last-child::before {
  left: 0;
  top: -1px;
}

.breadcrumb-wrapper li:last-child::after {
  left: -1px;
  top: 0;
}
.breadcrumb-wrapper li::before,
.breadcrumb-wrapper li::after {
  border-style: solid;
  width: 0;
  height: 0;
  content: '';
  position: absolute;
}
</style>
