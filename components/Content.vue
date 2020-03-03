<template>
  <div class="content-wrapper">
    <div v-for="(item, index) in items" :key="index" class="content">
      <div class="container">
        <div :class="{ inverted: item.layout_inverted }" class="row">
          <div class="col center-center"></div>
          <div class="col">
            <h2>{{ currentPage.title }}</h2>
            <p>{{currentPage.description}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: ["currentPage"],
  data() {
    return {
      items: [
        {
          layout_inverted: false,
          heading: "Leitbild",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          icon: "eimag-1--EN.svg"
        },
        {
          layout_inverted: false,
          heading: "Leitbild",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          icon: "eimag-1--EN.svg"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
.content {
  height: auto;
  display: flex;
  align-items: center;
  padding: 150px 0;
  min-height: 100vh;
  @media only screen and (max-width: 1240px) {
    padding: 130px 50px;
  }
  @media only screen and (max-width: 900px) {
    padding: 100px 30px;
  }
  @media only screen and (max-width: 500px) {
    padding: 80px 20px;
  }
}
.container {
  width: 1200px;
  margin: 0 auto;
  @media only screen and (max-width: 1240px) {
    width: 100%;
  }
}
.row {
  display: flex;
  margin: 0 -25px;
  &.inverted {
    flex-direction: row-reverse;
  }
  @media only screen and (max-width: 900px) {
    flex-wrap: wrap;
  }
}
.col {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 50%;
  margin: 0 25px;
  display: flex;
  justify-content: center;
  @media only screen and (max-width: 900px) {
    width: 100%;
    .iso-icon {
      max-width: 80%;
      margin-bottom: 30px;
    }
  }
}
h2 {
  font-family: "Open Sans";
  font-size: 64px;
  color: var(--dark);
  text-transform: uppercase;
  @media only screen and (max-width: 500px) {
    font-size: 42px;
  }
  @media only screen and (max-width: 330px) {
    font-size: 32px;
  }
}

.list {
  margin-bottom: 50px;
  &__item {
    display: flex;
    align-items: center;
    margin: 8px 0;
    img {
      margin-top: 1px;
      height: 16px;
      width: 20px;
      border-radius: 10px;
      margin-right: 8px;
    }
  }
}

.btn-group {
  margin-top: 30px !important;
  .btn {
    flex-grow: 0;
  }
}
</style>
