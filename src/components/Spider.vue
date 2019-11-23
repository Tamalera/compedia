<template>
  <div class="spider">
    <div class="web"></div>
    <div class="body">
      <div class="eyes">
        <div class="eye">
          <div class="pupil"></div>
        </div>
        <div class="eye">
          <div class="pupil"></div>
        </div>
      </div>
      <div class="mouth">
        <div class="fang"></div>
        <div class="fang"></div>
      </div>
      <div class="legs left">
        <div class="leg"></div>
        <div class="leg"></div>
        <div class="leg"></div>
        <div class="leg"></div>
      </div>
      <div class="legs right">
        <div class="leg"></div>
        <div class="leg"></div>
        <div class="leg"></div>
        <div class="leg"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "spider"
};
</script>

<style lang="scss" scoped>
$spider-color: #181818;
$spider-width: 100px;

/* body {
  font-family: "Roboto", sans-serif;
  padding: 0px;
  text-align: center;
  background: #7958b4;
} */

.spider {
  width: $spider-width;
  position: absolute;
  top: -60px;
  left: calc(50% - #{$spider-width/2});
  animation: web-bounce 0.75s ease-in-out infinite alternate;
}

.web {
  background: rgba(255, 255, 255, 0.5);
  width: 3px;
  height: 120px;
  margin: auto;
}

.body {
  display: block;
  width: $spider-width;
  height: 80px;
  background: $spider-color;
  border-radius: 50%;
  position: relative;
}

.eyes {
  position: absolute;
  top: 22px;
  width: 100%;
  display: flex;
  justify-content: center;
}

.eye {
  width: 21px;
  height: 24px;
  background: #fff;
  border-radius: 50%;
  margin: 0 5px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  .pupil {
    width: 8px;
    height: 8px;
    background: #000;
    border-radius: 50%;
  }

  &:first-of-type .pupil {
    margin-left: 3px;
  }
  &:last-of-type .pupil {
    margin-right: 3px;
  }
}

/* mouth */
.mouth {
  display: flex;
  justify-content: space-between;
  position: absolute;
  bottom: 12px;
  left: 28px;
  width: 45px;
  height: 10px;
  border-radius: 0% 0% 50% 50%;
  border: 0px solid rgba(255, 255, 255, 0.2);
  border-bottom-width: 10px;

  .fang {
    width: 0;
    height: 0;
    margin-top: 10px;
    border-style: solid;
    border-width: 12px 5px 0 5px;
    border-color: #ffffff transparent transparent transparent;
  }
}

.legs {
  position: absolute;
  top: 40px;
  display: block;
  width: 50px;
  z-index: -1;
  animation: 0.75s ease-in-out infinite alternate;

  .leg {
    position: absolute;
    border: 10px solid lighten($spider-color, 4%);
    border-bottom: 0;
    width: 40px;
    height: 30px;
  }

  &.left {
    left: -30px;
    animation-name: left-leg-wiggle;
    transform-origin: 100% 0%;
    .leg {
      transform-origin: 100% 0%;
      border-radius: 100% 0px 0px 0px;
      border-right: 0;

      @for $i from 0 through 3 {
        &:nth-child(#{$i + 1}) {
          transform: rotate(#{(($i * 30)-20)}deg);
        }
      }
    }
  }

  &.right {
    right: -30px;
    animation-name: right-leg-wiggle;
    transform-origin: 0% 0%;
    .leg {
      transform-origin: 0% 0%;
      border-radius: 0% 100% 0px 0px;
      border-left: 0;

      @for $i from 0 through 3 {
        &:nth-child(#{$i + 1}) {
          transform: rotate(#{(($i * 30)-20) * -1}deg);
        }
      }
    }
  }
}

@keyframes web-bounce {
  from {
    top: -20px;
  }
  to {
    top: 0;
  }
}

@keyframes left-leg-wiggle {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(5deg);
  }
}

@keyframes right-leg-wiggle {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-5deg);
  }
}
</style>
