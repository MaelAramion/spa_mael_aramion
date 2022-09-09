<template>
  <div class="content">
    <div class="article-content">
      <div v-if="id">
        <h2>{{ article.title }}</h2>
        <p>{{ article.body }}</p>
      </div>
      <div class="comments-container" v-if="id">
        <div class="commentaire" v-for="comment in this.comments " v-bind:key="comment">
          <h3 class="comment-name">{{ comment.name}}</h3>
          <h4><a class="email" href="malto:{{ comment.email }}">{{comment.email}}</a></h4>
          <div>
            <h4>Message : </h4>
            <p>{{ comment.body }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import axios from "axios";

export default {
  name: 'ArticleView',
  data () {
    return {
      id: null,
      article : [],
      comments:  [],
    }
  },
  created() {
    this.id = this.$route.params.id;
  },
  mounted(){
    axios
        .get('https://jsonplaceholder.typicode.com/posts/' + this.id)
        .then(response => (this.article = response.data))
    axios
        .get('https://jsonplaceholder.typicode.com/posts/' + this.id + '/comments')
        .then(response => (this.comments = response.data))
  }
}
</script>

<style>
.content{
  display: flex;
}
.article-content{
  margin: auto;
  width: 75%;
}
.commentaire{
  margin: 10px auto;
  padding: 10px;
  border-radius: 10px;
  width: 95%;
}
.comments-container{
  display: flex;
  flex-direction: column;
}
.commentaire h4{
  text-decoration: underline;
}
.content{
  padding: 10px;
}
.commentaire{
  width: 75%;
}
.comment-name{
  background: #fbc531;
  padding: 5px;
}
.email{
  color: #273c75;
}
</style>
