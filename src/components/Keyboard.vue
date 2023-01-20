<template>
  <div id="keyboard">
    <div class="row">
      <button data-key="q" @click="$emit('key-click', 'q')">q</button>
      <button data-key="w" @click="$emit('key-click', 'w')">w</button>
      <button data-key="e" @click="$emit('key-click', 'e')">e</button>
      <button data-key="r" @click="$emit('key-click', 'r')">r</button>
      <button data-key="t" @click="$emit('key-click', 't')">t</button>
      <button data-key="y" @click="$emit('key-click', 'y')">y</button>
      <button data-key="u" @click="$emit('key-click', 'u')">u</button>
      <button data-key="i" @click="$emit('key-click', 'i')">i</button>
      <button data-key="o" @click="$emit('key-click', 'o')">o</button>
      <button data-key="p" @click="$emit('key-click', 'p')">p</button>
    </div>
    <div class="row">
      <div class="spacer half"></div>
      <button data-key="a" @click="$emit('key-click', 'a')">a</button>
      <button data-key="s" @click="$emit('key-click', 's')">s</button>
      <button data-key="d" @click="$emit('key-click', 'd')">d</button>
      <button data-key="f" @click="$emit('key-click', 'f')">f</button>
      <button data-key="g" @click="$emit('key-click', 'g')">g</button>
      <button data-key="h" @click="$emit('key-click', 'h')">h</button>
      <button data-key="j" @click="$emit('key-click', 'j')">j</button>
      <button data-key="k" @click="$emit('key-click', 'k')">k</button>
      <button data-key="l" @click="$emit('key-click', 'l')">l</button>
      <div class="spacer half"></div>
    </div>
    <div class="row">
      <button data-key="↵" @click="$emit('enter-key-click')" class="one-and-a-half">enter</button>
      <button data-key="z" @click="$emit('key-click', 'z')">z</button>
      <button data-key="x" @click="$emit('key-click', 'x')">x</button>
      <button data-key="c" @click="$emit('key-click', 'c')">c</button>
      <button data-key="v" @click="$emit('key-click', 'v')">v</button>
      <button data-key="b" @click="$emit('key-click', 'b')">b</button>
      <button data-key="n" @click="$emit('key-click', 'n')">n</button>
      <button data-key="m" @click="$emit('key-click', 'm')">m</button>
      <button data-key="←" @click="$emit('backspace-key-click')" class="one-and-a-half">delete</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    keyClick() {

    }
  }
}
</script>

<style scoped lang="scss">
  #keyboard {
    width: 450px;
    margin: 0 auto;

    .row {
      display: flex;

      &:not(:last-child) {
        margin-bottom: 10px;
      }
    }
  }
  .half {
    flex: 0.5;
  }
  .one-and-a-half {
    flex: 1.5;
    font-size: 12px;
  }
  button {
    font-weight: bold;
    border: 0;
    padding: 0;
    margin: 0 6px 0 0;
    height: 58px;
    border-radius: 4px;
    cursor: pointer;
    user-select: none;
    background-color: #818384;
    color: #ffffff;
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    text-transform: uppercase;
    -webkit-tap-highlight-color: rgba(0,0,0,0.3);

    &[data-state='correct'] {
      border-color: #538d4e;
      background: #538d4e;
    }
    &[data-state='present'] {
      border-color: #b59f3b;
      background: #b59f3b;
    }
    &[data-state='nomatch'] {
      border-color: #888;
      background: #888;
    }
  }
</style>