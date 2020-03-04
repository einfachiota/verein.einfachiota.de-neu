<template>
  <div class="home">
    <Navigation
      v-bind:currentPage="currentPage"
      v-bind:currentPageId="currentPageId"
      @setCurrentPage="setCurrentPage"
    />
    <Illustration
      v-bind:currentPage="currentPage"
      v-bind:currentPageId="currentPageId"
      @setCurrentPage="setCurrentPage"
    />
    <Content v-bind:currentPage="currentPage" v-bind:currentPageId="currentPageId" />
    <button class="btn btn--primary next" @click="setCurrentPage(currentPageId+1)">Weiter</button>
  </div>
</template>

<script>
import Navigation from "../components/Navigation.vue";
import Illustration from "../components/Illustration.vue";
import Content from "../components/Content.vue";
export default {
  name: "index",
  components: { Navigation, Illustration, Content },
  data() {
    return {
      currentPageId: 0,
      pageStates: [
        {
          title: "Leitbild",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 0,
          visionState: {
            active: true,
            scale: 10,
            fill: 1
          },
          boardState: {
            active: false,
            scale: 0
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Vision",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 0,
          visionState: {
            active: true,
            scale: 10,
            fill: 0.25
          },
          boardState: {
            active: false,
            scale: 0
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Mission",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 0,
          visionState: {
            active: true,
            scale: 10,
            fill: 0.5
          },
          boardState: {
            active: false,
            scale: 0
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Ziele",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 0,
          visionState: {
            active: true,
            scale: 10,
            fill: 0.75
          },
          boardState: {
            active: false,
            scale: 0
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Werte",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 0,
          visionState: {
            active: true,
            scale: 10,
            fill: 1
          },
          boardState: {
            active: false,
            scale: 0
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Struktur",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 1,
          visionState: {
            active: false,
            scale: 1,
            fill: 1
          },
          boardState: {
            active: false,
            scale: 1
          },
          membersState: {
            active: false,
            scale: 1
          },
          communityState: {
            active: false,
            scale: 1
          }
        },
        {
          title: "Vorstand",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 1,
          visionState: {
            active: false,
            scale: 5,
            fill: 1
          },
          boardState: {
            active: true,
            scale: 1
          },
          membersState: {
            active: false,
            scale: 0
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Mitglieder",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 1,
          visionState: {
            active: false,
            scale: 3,
            fill: 1
          },
          boardState: {
            active: true,
            scale: 1.5
          },
          membersState: {
            active: false,
            scale: 1.25
          },
          communityState: {
            active: false,
            scale: 0
          }
        },
        {
          title: "Community",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 1,
          visionState: {
            active: false,
            scale: 1,
            fill: 1
          },
          boardState: {
            active: false,
            scale: 1
          },
          membersState: {
            active: false,
            scale: 1
          },
          communityState: {
            active: true,
            scale: 1
          }
        },
        {
          title: "Referate",
          description:
            "Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben. Unsere Vision ist es eine breite Öffentlichkeit um IOTA aufzubauen und die Anwendung von IOTA als Technologie voranzutreiben.",
          navState: 2,
          visionState: {
            active: false,
            scale: 1,
            fill: 1
          },
          boardState: {
            active: false,
            scale: 1
          },
          membersState: {
            active: false,
            scale: 1
          },
          communityState: {
            active: true,
            scale: 1
          }
        }
      ],
      currentPage: 0
    };
  },
  created() {
    this.setCurrentPage(0);
  },
  methods: {
    setCurrentPage(id) {
      if (id >= this.pageStates.length) {
        this.currentPageId = 0;
        this.currentPage = this.pageStates[0];
      } else {
        this.currentPageId = id;
        this.currentPage = this.pageStates[id];
      }
    }
  }
};
</script>

<style lang="scss">
.btn-group {
  display: flex;
  justify-content: space-between;
  margin: 0 -15px;
  .btn {
    flex-grow: 1;
    margin: 0 15px;
  }
}

.btn {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 40px;
  padding: 0 30px;
  background-color: var(--light);
  border-radius: 50px;
  font-weight: 900;
  font-size: 14px;
  text-decoration: none;
  transition: var(--transition);
  outline: none;
  border: none;
  img {
    margin-right: 8px;
  }
  &:hover {
    cursor: pointer;
  }
  &--primary {
    color: var(--white);
    background-color: var(--primary);
    &:hover {
      background-color: var(--primary_light);
    }
  }
  &--secondary {
    color: var(--dark);
    background-color: var(--light);
    &:hover {
      background-color: var(--light_50);
    }
  }
  &.next {
    position: fixed;
    bottom: 50px;
    right: 50px;
    z-index: 100;
  }
}

// S C R O L L B A R   S T Y L E S
::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  background: var(--light);
}
::-webkit-scrollbar-thumb {
  background-color: var(--primary_50);
  border-radius: 5px;
  transition: all 0.3s ease-in-out;
}
::-webkit-scrollbar-thumb:hover {
  background-color: var(--primary);
}
</style>
