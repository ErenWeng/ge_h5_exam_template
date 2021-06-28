<template>
  <div class="home">
    <button @click="popup('test')">跳出彈跳視窗</button>
    <Popup
      v-if="popupOpen === 'test'"
      :user-title="userTitle"
      :user-content="userContent"
      @add="add"
      @close="close"
    >
      <template slot="title" slot-scope="title">
        <p>title: {{ title.data }}</p>
      </template>
      <template slot="content" slot-scope="content">
        <p>content: {{ content.data }}</p>
        <p>count: {{ $store.state.count }}</p>
      </template>
    </Popup>
    <div>
      title:
      <input v-model="userTitle" type="text" placeholder="請輸入 title" />
    </div>
    <div>
      content:
      <input v-model="userContent" type="text" placeholder="請輸入 content" />
    </div>
    <p>count: {{ $store.state.count }}</p>
  </div>
</template>

<script>
// @ is an alias to /src
import Popup from "@/components/Popup.vue";

export default {
  name: "Home",
  components: {
    Popup,
  },
  data() {
    return {
      popupOpen: "",
      userTitle: "",
      userContent: "",
    };
  },
  methods: {
    popup(target) {
      this.popupOpen = target;
    },
    close() {
      this.popupOpen = "";
    },
    add() {
      this.$store.commit("addCount");
    },
  },
};
</script>
