<template>
  <div class="popup" v-bind:class="{ 'is-active': active }" id="popup-main">
    <div class="popup-overlay popup-button" data-target="#popup-main"></div>
    <div class="popup-inner">
      <h2>Add new Blog</h2>
      <form>
        <input type="text" placeholder="blog title" />
        <input type="text" placeholder="blog content" />
        <button @click.prevent="addBlog">Submit</button>
      </form>
      <button
        @click="toggleModal"
        class="button popup-button"
        data-target="#popup-main"
      >
        Close
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Modal",
  props: {
    active: Boolean,
    toggleModal: Function,
  },
  methods: {
    addBlog: function () {
      console.log("submitted");
      this.toggleModal();
    },
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

.page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.button {
  appearance: none;
  border: none;
  outline: none;

  display: inline-block;
  background-color: #fe4880;
  color: #fff;
  font-size: 20px;
  padding: 10px 15px;
  border-radius: 8px;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  margin: 0px 15px;
}

.button.large {
  font-size: 24px;
  padding: 15px 30px;
}

.popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 999;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.4s;
}

.popup.is-active {
  opacity: 1;
  pointer-events: all;
}

.popup-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  background-color: rgba(0, 0, 0, 0.5);
}

.popup-inner {
  position: relative;
  z-index: 1;
  max-width: 600px;
  padding: 50px 30px;
  background-color: #fff;
  border-radius: 16px;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.1);
}

.popup h2 {
  color: #313131;
  font-size: 28px;
  font-weight: 600;
}

.popup h3 {
  color: #888;
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 30px;
}

.popup p {
  color: #666;
  font-size: 16px;
  font-weight: 400;
  margin-bottom: 15px;
}

.popup p:last-of-type {
  margin-bottom: 30px;
}
</style>
