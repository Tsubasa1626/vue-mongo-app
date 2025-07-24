<template>
  <div class="hello">
    <h1>📦 MongoDBのデータ一覧</h1>
    <ul>
      <li v-for="note in notes" :key="note._id">
        <strong>{{ note.title }}</strong> - {{ note.content }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data() {
    return {
      notes: []
    }
  },
  mounted() {
    axios.get("http://153.120.121.157:3000/notes_from_b")
      .then(response => {
        this.notes = response.data
      })
      .catch(error => {
        console.error("API接続エラー:", error)
      })
  }
}
</script>

<style scoped>
h1 {
  color: #2c3e50;
  margin-bottom: 20px;
}
ul {
  padding-left: 0;
  list-style-type: none;
}
li {
  background: #f9f9f9;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 6px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}
</style>
