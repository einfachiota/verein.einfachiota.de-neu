<template>
  <StyledIllustration>
    <img
      src="@/assets/vision.png"
      alt=""
      class="vision"
      :style="{ transform: 'scale(' + visionScaleMultiplier + ')' }"
    />
    <div class="board"></div>
    <div class="members"></div>
    <div class="community"></div>
    <div class="departments"></div>
  </StyledIllustration>
</template>

<script>
import vision from "../assets/vision.png";
import styled from "vue-styled-components";
const StyledIllustration = styled.div`
  position: fixed;
  right: calc(50% + 25px);
  top: 50%;
  transform: translateY(-50%);
  min-height: 500px;
  width: 500px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  .vision {
    height: 50px;
    width: 50px;
    transition: all 0.3s ease-in-out;
  }
`;

export default {
  components: { StyledIllustration },
  data() {
    return {
      innerHeight: 0,
      scrollY: 0,
      scrollPercentage: 0,
      visionScaleMultiplier: 0
    };
  },

  mounted() {
    console.log("scrollY", this.scrollY);
    if (process.client) {
      this.innerHeight = window.innerHeight;
      console.log("innerHeight", window.innerHeight);
      document.addEventListener("scroll", this.onScroll);
    }
  },
  methods: {
    onScroll() {
      if (process.client) {
        this.scrollY = window.scrollY;
        this.scrollPercentage = this.scrollY / this.innerHeight;
        this.visionScaleMultiplier = 1 + this.scrollPercentage * 9;
      }
    }
  }
};
</script>
