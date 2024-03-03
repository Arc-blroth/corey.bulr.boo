<style lang="scss">
  @import 'https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400&family=Noto+Emoji:wght@700&display=swap';

  @font-face {
    font-family: Weezer;
    src: url("/weezerfont.ttf");
  }

  .bg {
    width: 100%;
    height: 100%;
    background-color: black;
    font-family: Weezer, sans-serif;
    user-select: none;
  }

  .wheeze {
    display: flex;
    flex-flow: column-reverse;

    --w: min(calc(0.8 * min(100vw, 100vh)), 512px);

    width: var(--w);
    height: var(--w);
    transform: translate(calc(50vw - var(--w) / 2), calc(50vh - var(--w) / 2));
    background-color: #019ad3;
    font-size: calc(var(--w) / 8);
    line-height: calc(var(--w) / 8);
    color: white;

    .four {
      font-family: "Noto Emoji", sans-serif;
      text-align: center;

      & > span:nth-child(1) {
        color: yellow;
      }

      & > span:nth-child(2) {
        color: orange;
      }

      & > span:nth-child(3) {
        color: red;
      }

      & > span:nth-child(4) {
        color: greenyellow;
      }
    }

    .punch {
      text-align: right;
      margin: 0.35ch 0.55ch 0 0;
      flex-grow: 1;
    }
  }
</style>

<div class="bg">
  <div class="wheeze">
    <div class="four">
      <span>🍋</span>
      <span>🍊</span>
      <span>🍎</span>
      <span>🍈</span>
    </div>
    <p class="punch">emojeezer</p>
  </div>
</div>
