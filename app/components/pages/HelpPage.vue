<template>
  <div class="help-container">
    <app-header showDefaultHeaderNav showOnlySessionLinks/>
    <div class="area-help">
      <h1 class="title">お問い合わせ</h1>
      <p class="description">
        クローズドβ版のため、ご不便をおかけいたしております。
        問い合わせでいただいた内容は確認次第ご返信させていただきます。
      </p>
      <app-button class="sendmail-button">
        <a href="mailto:info@alismedia.jp?subject=お問い合わせ">
          問い合わせメールを送る
        </a>
      </app-button>
    </div>
    <app-footer/>
  </div>
</template>

<script>
import AppButton from '../atoms/AppButton'
import AppHeader from '../organisms/AppHeader'
import AppFooter from '../organisms/AppFooter'

export default {
  components: {
    AppButton,
    AppHeader,
    AppFooter
  }
}
</script>

<style lang="scss" scoped>
.help-container {
  display: grid;
  grid-template-rows: 100px 150px calc(100vh - 100px - 150px - 75px) 75px;
  grid-template-columns: 1fr 600px 1fr;
  /* prettier-ignore */
  grid-template-areas:
    'app-header       app-header       app-header      '
    '...              ...              ...             '
    '...              help             ...             '
    'app-footer       app-footer       app-footer      ';
  background: white;
}

.area-help {
  grid-area: help;
}

.title {
  color: #030303;
  font-size: 14px;
  font-weight: 500;
  line-height: 21px;
  text-align: center;
}

.description {
  @include default-text();
}

.sendmail-button {
  margin: 60px auto 0;
}

@media screen and (max-width: 640px) {
  .help-container {
    grid-template-rows: 70px 10vh calc(100vh - 10vh - 70px - 190px) min-content;
    grid-template-columns: 30px 1fr 30px;
    /* prettier-ignore */
    grid-template-areas:
    'app-header       app-header       app-header      '
    '...              ...              ...             '
    '...              help             ...         '
    'app-footer       app-footer       app-footer      ';
  }

  .description {
    color: #6e6e6e;
    font-size: 12px;
    font-weight: 500;
    line-height: 18px;
  }
}
</style>
