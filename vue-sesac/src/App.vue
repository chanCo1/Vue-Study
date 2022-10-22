<template>
  <div>
    <!-- TODO: 데이터 바인딩 -->
    <div>Hello {{ userName }}</div>
    <h1 class="title">This is Title.</h1>
    <h2 :class="dynamic">??</h2>
    <img :src="image.src" :alt="image.alt" />

    <!-- TODO: CSS클래스 -->
    <h2 :class="isDone ? 'line-through' : 'highlight'">line-through</h2>
    <h2 :class="textDecoration">line-through</h2>
    <p :class="{ highlight: isDone, 'text-red': userName === 'chanCo' }">요요</p>
    <p :class="['content', userName === 'chanCo' ? 'green' : 'line-through']">ㅋㅋㅋㅋㅋㅋ</p>

    <!-- TODO: 조건부 렌더링 -->
    <h2 v-once v-text="user.name"></h2>
    <h2 v-text="user.name"></h2>
    <input type="text" v-model="user.name" />

    <p v-if="user.name === 'chanCo'">{{ user.job }}</p>
    <p v-else>이름을 보여줄 수 없다</p>

    <p v-if="showName">{{ user.name }} IF</p>
    <p v-show="showName">{{ user.name }} 이건 css를 건들여서 display: none 처리를 함</p>

    <ul>
      <template v-if="question === 'frontend'">
        <li>HTML</li>
        <li>CSS</li>
        <li>JS</li>
      </template>
      <template v-else>
        <li>JAVA</li>
        <li>PYTHON</li>
        <li>C#</li>
      </template>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      userName: 'chanCo',
      dynamic: 'content',
      image: {
        src: 'https://placeimg.com/200/200/any',
        alt: 'randome image'
      },
      textDecoration: 'line-through',
      isDone: true,
      user: {
        name: 'chanCo',
        age: 100,
        job: 'developer'
      },
      showName: true,
      question: 'frontend'
    };
  },
  components: {}
};
</script>

<style>
.title {
  color: red;
  background-color: yellow;
}

.content {
  color: blue;
  background-color: pink;
}

.line-through {
  text-decoration: line-through;
}

.highlight {
  background-color: red;
  color: #fff;
}

.text-red {
  color: cyan;
}

.green {
  color: green;
}
</style>
