<template>
  <div class="grid">
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
    <div class="grid-row">
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
      <div class="grid-row__item" data-state="empty"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Grid',
  props: {},
}
</script>

<style scoped lang="scss">
.grid {
  width: 350px;
  height: 400px;
  margin: 0 auto 50px auto;

  &-row {
    width: 100%;
    display: flex;

    &:not(:last-child) {
      margin-bottom: 8px;
    }

    &__item {
      width: 20%;
      height: 52px;
      display: block;
      margin: 0 4px;
      border: 2px solid #444;
      font-size: 30px;
      color: #fff;
      font-weight: bold;
      text-align: center;
      line-height: 46px;
      text-transform: uppercase;
      transition: all .2s ease;

      &[data-state='tbd'] {
        border-color: #888;
      }
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
  }
}
</style> 
