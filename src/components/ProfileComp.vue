<template>
  <section class="profile">
    <img
      class="profile__image"
      src="@/assets/img/waiter.png"
      alt="Waiter Photo"
    />
    <div class="profile__info">
      <strong class="profile__name">Philip</strong>
      <span class="profile__role">was your waiter</span>
      <div class="profile__logo">
        <img
          class="profile__logo-logo"
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
            <text font-size="9">
              <!-- Размер шрифта может потребовать дополнительной корректировки -->
              <textPath xlink:href="#circle">
                Powered by TImpl * Powered by TImpl * Powered by TImpl *
                <!-- Регулируйте количество повторений текста для достижения оптимального размещения -->
              </textPath>
            </text>
          </svg>
        </div>
      </div>
      <div class="profile__logo-wrap">
        <div class="profile__logo">
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
            <text font-size="9">
              <!-- Размер шрифта может потребовать дополнительной корректировки -->
              <textPath xlink:href="#circle">
                Powered by TImpl * Powered by TImpl * Powered by TImpl *
                <!-- Регулируйте количество повторений текста для достижения оптимального размещения -->
              </textPath>
            </text>
          </svg>
        </div>
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

  &::before {
    position: absolute;
    bottom: 0;
    left: 8px;
    z-index: -1;
    width: 326px;
    height: 149px;
    background: #7c36c5;
    border-radius: 52.5px;
    filter: blur(35px);
    content: '';
  }

  &__image {
    border-radius: 28px;
  }

  &__info {
    position: absolute;
    bottom: 47px;
    left: -30px;
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 256px;
    padding-top: 24px;
    padding-bottom: 19px;
    padding-left: 38px;
    color: #fff;
    background: #8e6cea;
    border-radius: 8px;

    &::before {
      position: absolute;
      bottom: -17px;
      left: 0;
      z-index: -1;
      width: 100%;
      max-width: 91px;
      height: 83px;
      background: #6238d3;
      border-radius: 6px;
      content: '';
    }
  }

  &__name {
    font-size: 24px;
  }

  &__role {
    font-size: 13px;
  }

  &__logo {
    &-wrap {
      position: absolute;
      inset: 0;
      overflow: hidden;

      .profile__logo {
        color: #96ff43;
      }
    }

    position: absolute;
    right: -130px;
    bottom: -75px;
    z-index: 5;
    width: 193px;
    height: 193px;
    color: #8e6cea;
    font-size: 13px;

    &-logo {
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
