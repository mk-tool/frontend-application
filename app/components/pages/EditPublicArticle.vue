<template>
  <div class="edit-article-container">
    <app-header showEditHeaderNav showPostArticleLink/>
    <article-editor :title="title" :putArticle="this.putArticle"/>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import AppHeader from '../organisms/AppHeader'
import ArticleEditor from '../atoms/ArticleEditor'

export default {
  components: {
    AppHeader,
    ArticleEditor
  },
  computed: {
    ...mapGetters('article', ['title', 'body', 'thumbnail'])
  },
  methods: {
    ...mapActions('article', ['putPublicArticle', 'gotArticleData']),
    async putArticle() {
      if (!this.gotArticleData) return
      const { title, body, thumbnail } = this
      const { articleId } = this.$route.params
      const article = { title, body }
      if (thumbnail !== '') article.eye_catch_url = thumbnail
      await this.putPublicArticle({ article, articleId })
    }
  }
}
</script>

<style lang="scss" scoped>
.edit-article-container {
  display: grid;
  grid-template-rows: 100px 50px 650px 75px;
  grid-template-columns: 1fr 640px 1fr;
  /* prettier-ignore */
  grid-template-areas:
    "app-header  app-header app-header"
    "...         ...        ...       "
    "...         editor     ...       "
    "...         ...        ...       ";
}
</style>
