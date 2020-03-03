<template>
  <StyledIllustration>
    <div
      class="vision"
      @click="setCurrentPage(1)"
      :id="1"
      :style="{ transform: 'scale(' + this.currentPage.visionState.scale + ')' }"
    ></div>
    <div class="board" :style="{ transform: 'scale(' + this.currentPage.boardState.scale + ')' }" />
    <div
      class="members"
      :style="{ transform: 'scale(' + this.currentPage.membersState.scale + ')' }"
    />
    <div
      class="community"
      :style="{ transform: 'scale(' + this.currentPage.communityState.scale + ')' }"
    />
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
  .vision,
  .board,
  .members,
  .community {
    position: absolute;
    border-radius: 50%;
    border: 0px solid var(--primary);
    transition: all 0.3s ease-in-out;
    background-color: rgba(0, 183, 197, 0.25);
    &:hover {
      background-color: rgba(0, 183, 197, 0.5);
    }
    &.active {
      height: 500px;
      width: 500px;
    }
  }
  .vision {
    z-index: 14;
    height: 40px;
    width: 40px;
  }
  .board {
    z-index: 12;
    height: 200px;
    width: 200px;
  }
  .members {
    z-index: 11;
    height: 350px;
    width: 350px;
  }
  .community {
    z-index: 10;
    height: 500px;
    width: 500px;
  }
`;
export default {
  components: { StyledIllustration },
  props: ["currentPage", "currentPageId"],
  data() {
    return {
      pageData: 0,
      innerHeight: 0,
      scrollY: 0,
      scrollPercentage: 0,
      visionScaleMultiplier: 0
    };
  },
  mounted() {
    if (process.client) {
      this.innerHeight = window.innerHeight;
      document.addEventListener("scroll", this.onScroll);
    }
  },
  methods: {
    setCurrentPage(id) {
      this.$emit("setCurrentPage", id);
    },
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
