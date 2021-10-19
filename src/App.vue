<template>
  <div class="container">
    <div class="wrapper-flex">
      <div class="sidebar">
        <div class="sidebar__video">
          <div class="accordion">
            <div class="accordion__trigger" @click="accordionTrigger">
              Відео
            </div>
            <div class="accordion__content accordion__content--video">
              <label class="accordion__lable">
                <input
                  type="checkbox"
                  name="sale"
                  id="sale"
                  class="accordion__input"
                />
                <span class="accordion__text"> Акція </span>
              </label>
              <label class="accordion__lable">
                <input
                  type="checkbox"
                  name="popular"
                  id="popular"
                  class="accordion__input"
                />
                <span class="accordion__text"> Популярні </span>
              </label>
              <label class="accordion__lable">
                <input
                  type="checkbox"
                  name="news"
                  id="news"
                  class="accordion__input"
                />
                <span class="accordion__text"> Новинки </span>
              </label>
            </div>
          </div>
        </div>
        <div class="sidebar__theme">
          <div class="accordion">
            <div class="accordion__trigger" @click="accordionTrigger">Темы</div>
            <div class="accordion__content accordion__content--theme">
              <span class="accordion__text"> Всі теми (25) </span>
              <span class="accordion__text"> Акцизний подарок (4) </span>
              <span class="accordion__text"> Валюта (9) </span>
              <span class="accordion__text">
                Виробництво і собівартість (7)
              </span>
              <span class="accordion__text"> Відпустки (8) </span>
              <span class="accordion__text"> Відрядження (7) </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  methods: {
    accordionTrigger(element) {
      const parent = element.target.parentNode;
      parent.classList.toggle("accordion__active");
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/_mixin.scss";

.wrapper-flex {
  z-index: 0;
}
.sidebar {
  background-color: $while;
  box-shadow: 0px 0px 11px 5px rgba(35, 35, 35, 0.2);
  width: 278px;
  height: 100vh;
  padding: 30px 15px;
}
.sidebar__video {
}
.accordion {
  position: relative;
  overflow: hidden;
  border-radius: 10px;
  transition: 1s;
}
.accordion__trigger {
  border: 1px solid $grey;
  // border-bottom: none;
  // border-top-left-radius: 10px;
  // border-top-right-radius: 10px;
  border-radius: 10px;
  background-color: $grey;
  padding: 10px 45px;
  position: relative;
  cursor: pointer;
  transition: 1s;
  z-index: 1;
  &:before {
    content: "";
    position: absolute;
    top: 13px;
    left: 17px;
    width: 20px;
    height: 20px;
    background-image: url("./assets/images/video-palay.png");
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
  }
  &:after {
    content: "";
    position: absolute;
    top: 18px;
    right: 20px;
    width: 16px;
    height: 10px;
    background-image: url("./assets/images/icons-arrow.png");
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
    transform: rotateY(0deg) rotate(-90deg);
    transition: 0.5s;
  }
}
.accordion__content {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  flex-direction: column;
  padding: 15px 20px;
  transition: 1s;
  height: 0;
  border: 1px solid $grey;
  border-top: none;
  border-bottom-right-radius: 10px;
  border-bottom-left-radius: 10px;
}

.accordion__content.accordion__content--video {
  transform: translateY(-200px);
}
.accordion__content.accordion__content--theme {
  transform: translateY(-300px);
}

.accordion.accordion__active > .accordion__content.accordion__content--video {
  transform: translateY(0px);
  transition: 1s;
  height: 108px;
}
.accordion.accordion__active > .accordion__content.accordion__content--theme {
  transform: translateY(0px);
  transition: 1s;
  height: 100%;
}
.accordion.accordion__active > .accordion__trigger {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}
.accordion.accordion__active > .accordion__trigger::after {
  transform: rotateY(0deg) rotate(0deg);
}
.accordion__lable {
}
.accordion__input {
}
.accordion__text {
}
.sidebar__theme {
  margin: 15px 0 0 0;
}
</style>
