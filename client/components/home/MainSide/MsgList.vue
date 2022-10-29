<template>
  <div>
    <ul>
      <li v-for="item in postData" :key="item._id" class="mt-5">
        <MsgListItem :post="item" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["postData"],
  components: {
    MsgListItem: () => import("@/components/home/MainSide/MsgListItem.vue"),
  },
};
</script>
