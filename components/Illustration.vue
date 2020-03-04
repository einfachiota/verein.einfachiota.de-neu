<template>
  <StyledIllustration>
    <div
      class="vision"
      @click="setCurrentPage(1)"
      :id="1"
      :style="{ transform: 'scale(' + this.currentPage.visionState.scale + ')' }"
    >
      <div class="vision-overlay" :style="{ height: this.currentPage.visionState.fill + '%' }" />
    </div>
    <div
      class="board"
      :style="{ transform: 'scale(' + this.currentPage.boardState.scale + ')' }"
      @click="setCurrentPage(6)"
    />
    <div
      class="members"
      :style="{ transform: 'scale(' + this.currentPage.membersState.scale + ')' }"
      @click="setCurrentPage(7)"
    />
    <div
      class="community"
      :style="{ transform: 'scale(' + this.currentPage.communityState.scale + ')' }"
      @click="setCurrentPage(8)"
    />
    <div class="departments">
      <div
        class="department"
        v-for="item in departmentsData"
        :key="item.id"
        v-bind:class="{active: currentPage.departmentState.active, focus: currentPage.departmentState.activeDepartmentId === item.id}"
        @click="setCurrentPage(item.pageId)"
      >
        <img src alt />
      </div>
    </div>
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
  .community,
  .department {
    position: absolute;
    border-radius: 50%;
    border: 0px solid var(--primary);
    transition: all 0.3s ease-in-out;
    background-color: rgba(0, 183, 197, 0.25);
    cursor: pointer;
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
    overflow: hidden;
    .vision-overlay {
      position: absolute;
      bottom: 0;
      height: 100%;
      width: 40px;
      background-color: var(--primary);
      transition: all 0.3s ease-in-out;
    }
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
  .departments {
    .department {
      z-index: 15;
      height: 50px;
      width: 50px;
      border-radius: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      transform: scale(0);
      &.active {
        transform: scale(1);
      }
      &.focus {
        background-color: var(--primary);
      }
      &:nth-child(1) {
        top: 225px;
        left: 225px;
        &.active {
          top: -25px;
          left: 225px;
        }
      }
      &:nth-child(2) {
        top: 225px;
        right: 225px;
        &.active {
          top: 69px;
          right: 29px;
        }
      }
      &:nth-child(3) {
        bottom: 225px;
        right: 225px;
        &.active {
          bottom: 169px;
          right: -19px;
        }
      }
      &:nth-child(4) {
        bottom: 225px;
        right: 225px;
        &.active {
          bottom: 0;
          right: 116px;
        }
      }
      &:nth-child(5) {
        bottom: 225px;
        left: 225px;
        &.active {
          bottom: 0;
          left: 116px;
        }
      }
      &:nth-child(6) {
        bottom: 225px;
        left: 225px;
        &.active {
          bottom: 169px;
          left: -19px;
        }
      }
      &:nth-child(7) {
        top: 225px;
        left: 225px;
        &.active {
          top: 69px;
          left: 29px;
        }
      }
    }
  }
`;
export default {
  components: { StyledIllustration },
  props: ["currentPage", "currentPageId"],
  data() {
    return {
      departmentsData: [
        {
          id: 0,
          name: "Vorsitz",
          icon: "",
          pageId: 10
        },
        {
          id: 1,
          name: "Finanzen",
          icon: "",
          pageId: 11
        },
        {
          id: 2,
          name: "Community",
          icon: "",
          pageId: 12
        },
        {
          id: 3,
          name: "Events",
          icon: "",
          pageId: 13
        },
        {
          id: 4,
          name: "Design",
          icon: "",
          pageId: 14
        },
        {
          id: 5,
          name: "Development",
          icon: "",
          pageId: 15
        },
        {
          id: 6,
          name: "Redaktion",
          icon: "",
          pageId: 16
        }
      ],
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
