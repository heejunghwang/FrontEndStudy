<template>
  <section class="container">
    <div>
      <h1 class="title">
        테스트
      </h1>

      <!-- 검색 영역-->
      <div>
        <form class="form-inline">
          <div class="form-group">
            <p class="form-control-static">* 검색</p>
          </div>
          <div class="form-group mx-sm-3">
            <input type="text" class="form-control" placeholder="검색어를 입력하세요">
          </div>
          <button type="submit" class="btn btn-primary">검색</button>
        </form>
      </div>

      <table class="table">
        <thead>
        <tr>
          <th>#</th>
          <th>First Name</th>
          <th>Last Name</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="item in list">
          <th scope="row">1</th>
          <td>{{item.name}}</td>
          <td>{{item.age}}</td>
        </tr>
        </tbody>
      </table>

    </div>
  </section>
</template>

<script>
  import axios from 'axios'

  export default {
    asyncData () {
      return axios.get('https://api.myjson.com/bins/7fo5p')
        .then((res) => {
          return {list: res.data}
        })
    },
    computed: {

    },
    methods: {

    }
  }
</script>

<style>

</style>
