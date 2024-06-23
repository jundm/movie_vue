<template>
  <div class="search-box">
    <!--           @input="inputText=$event.target.value"-->
    <!--           v-model="inputText"-->
    <input type="search"
           @change="
           $emit('searchMovie',$event.target.value);
           inputText = $event.target.value;
           $event.target.value = ''
           "
           placeholder="검색어 입력">
    <button>검색</button>
  </div>
  <p>{{ inputText }}</p>
</template>

<script>
export default {
  name: "SearchBarComponent",
  data() {
    return {
      inputText: "",
    };
  },
  props: {
    data: Array,
  },
  watch: {
    // (변경값,이전값)
    inputText(name) {
      // 입력한 영화제목이 데이터에 있는지 확인
      const findName = this.data.filter(movie => {
        return movie.title.includes(name);
      });
      if (findName.length == 0) {
        alert("자료 없어요");
      }
    }
  }
};
</script>

<style>
.search-box {
  padding: 10px;
  display: flex;
  justify-content: center;
}

.search-box input {
  padding: 5px 10px;
}

.search-box button {
  margin: 0;
}
</style>