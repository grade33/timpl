<template>
  <section class="profile">
    <div class="profile__image-wrap">
      <img
        class="profile__image"
        src="@/assets/img/waiter.png"
        alt="Waiter Photo"
      />
    </div>
    <div class="profile__info">
      <div class="profile__info-sign-forward">
        <div class="profile__logo">
          <img
            class="profile__logo-icon"
            src="@/assets/img/wheel-logo.png"
            alt="Waiter working company logo - Теремок"
          />
          <div class="profile__logo-text-wrapper">
            <svg
              class="profile__logo-text"
              viewBox="0 0 193 193"
              width="193"
              height="193"
            >
              <defs>
                <path
                  id="circle"
                  d="
          M 96.5, 96.5
          m -73, 0
          a 73,73 0 1,1 146,0
          a 73,73 0 1,1 -146,0"
                />
              </defs>
              <text>
                <textPath xlink:href="#circle">
                  Powered by TImpl * Powered by TImpl * Powered by TImpl *
                </textPath>
              </text>
            </svg>
          </div>
        </div>
        <div class="profile__logo-wrap">
          <div class="profile__logo">
            <div class="profile__logo-text-wrapper">
              <svg
                class="profile__logo-text"
                viewBox="0 0 193 193"
                width="193"
                height="193"
              >
                <defs>
                  <path
                    id="circle"
                    d="
                M 96.5, 96.5
                m -73, 0
                a 73,73 0 1,1 146,0
                a 73,73 0 1,1 -146,0"
                  />
                </defs>
                <text>
                  <textPath xlink:href="#circle">
                    Powered by TImpl * Powered by TImpl * Powered by TImpl *
                  </textPath>
                </text>
              </svg>
            </div>
          </div>
        </div>
      </div>
      <div class="profile__info-sign-backward"></div>
      <div class="profile__text">
        <strong class="profile__name">Philip</strong>
        <span class="profile__role">was your waiter</span>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.profile {
  position: relative;
  z-index: 1;

  &__image {
    &-wrap {
      position: relative;
      z-index: -1;
      height: 400px;
      overflow: hidden;
      border-radius: 28px;

      &::before {
        position: absolute;
        right: 0;
        bottom: -40px;
        left: -10px;
        z-index: 2;
        width: 150%;
        height: 60px;
        background: #b8b6f4;
        transform: rotate(-5deg);
        content: '';
      }
    }

    position: absolute;
    bottom: -8px;
    left: 50%;
    width: auto;
    max-width: none;
    max-height: none;
    border-radius: 28px;
    transform: translateX(-50%);
  }

  &__info {
    position: absolute;
    bottom: 70px;
    left: 0;
    width: 100%;
    color: #fff;

    &-sign-backward {
      position: absolute;
      bottom: -36px;
      left: -41px;
      z-index: -2;
      width: 122px;
      height: 83px;
      background: #6238d3;
      border-radius: 6px;
      transform: rotate(-172deg);
      content: '';
    }

    &-sign-forward {
      position: absolute;
      bottom: -19px;
      left: -63px;
      width: 290px;
      height: 88px;
      background: #8e6cea;
      border-radius: 8px;
      transform: rotate(-5deg);
      content: '';
    }
  }

  &__text {
    position: relative;
    z-index: 5;
    display: flex;
    flex-direction: column;
    padding-left: 28px;
  }

  &__name {
    font-size: 24px;
  }

  &__role {
    font-size: 13px;
  }

  &__logo {
    position: absolute;
    right: -129px;
    bottom: -95px;
    z-index: 5;
    width: 193px;
    height: 193px;
    color: #8e6cea;
    font-size: 13px;
    transform: rotate(5deg);

    &-wrap {
      position: absolute;
      overflow: hidden;
      inset: 0;

      .profile__logo {
        color: #96ff43;
      }
    }

    &-icon {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    &-text {
      &-wrapper {
        height: 144px;
        overflow: hidden;
        transform: rotate(-5deg);
      }

      min-width: 193px;
      min-height: 193px;
      font-size: inherit;
      text-transform: uppercase;
      transform-origin: center;
      animation: rotate-center 15s linear infinite;
      fill: currentcolor;

      @keyframes rotate-center {
        from {
          transform: rotate(0deg);
        }

        to {
          transform: rotate(360deg);
        }
      }
    }
  }
}
</style>
