<template>
  <div class="wrap">
    <aside :class="[{ open: isOpen }, 'aside']">
      <div class="aside__togle-button" @click="isOpen = !isOpen">
        <span>
          <svg
            class="arr"
            width="8"
            height="12"
            viewBox="0 0 8 12"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect
              x="5.77817"
              width="2"
              height="8"
              transform="rotate(45 5.77817 0)"
              fill="#6FBC9A"
            />
            <rect
              x="7.19238"
              y="9.89954"
              width="2"
              height="8"
              transform="rotate(135 7.19238 9.89954)"
              fill="#6FBC9A"
            />
          </svg>
        </span>
      </div>
      <Aside :isOpen="isOpen" />
    </aside>
    <main class="main">
      <Nuxt />
    </main>
  </div>
</template>

<script>
import Aside from "../components/Aside";

export default {
  components: {
    Aside
  },
  data() {
    return {
      isOpen: false,
      window: {
        width: 0
      }
    };
  },
  created() {
    if (process.browser) {
      window.addEventListener("resize", this.handleResize);
    }
    this.handleResize();
  },
  methods: {
    handleResize() {
      if (process.browser) {
        if (window.innerWidth < 1200) {
          this.isOpen = true;
        } else {
          this.isOpen = false;
        }
        this.window.width = window.innerWidth;
      }
    }
  }
};
</script>

<style lang="scss">
@import "~/assets/scss/style.scss";
.aside {
  width: 16rem;
  padding: $space-lg $space-xl;
  position: relative;

  transition: all 0.3s;

  &.open {
    width: 5rem;
    padding: $space-lg 1.5rem;

    & .arr {
      transition: all 0.3s;
      transform: rotate(180deg);
    }
  }
  &__togle-button {
    position: absolute;
    right: -21px;
    background: $white;
    top: 0.875rem;
    box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.15);
    @include flex_all_center;
    border-radius: 100%;
    height: 40px;
    width: 40px;
    padding: $space-md;
    transition: transform 0.3s;
    cursor: pointer;
    animation: common infinite 1s cubic-bezier(0.075, 0.82, 0.165, 1);

    @keyframes common {
      from {
        transform: translateX(-3px);
      }
      to {
        transform: translateX(0);
      }
    }

    &:hover {
      transform: translateX(-5px);
    }
  }
}
.wrap {
  display: flex;
  height: 100vh;
}

.main {
  flex: 1;
  background-color: $body-color;
}
</style>
