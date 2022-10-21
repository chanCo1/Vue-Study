<template>
  <div>
    <!-- TODO: 데이터 바인딩 -->
    <h1>Hello {{ animail }}!</h1>
    <h2>{{ food }}</h2>

    <input type="text" v-model="food" />

    <p v-html="message" />

    <img :src="image" alt="random" />

    <h2 :class="{ red: food === 'apple', 'not-good': food === 'rice' }">
      원숭이는 {{ food }}를 좋아합니다.
    </h2>

    <a :href="food">{{ food }}</a>

    <hr />

    <!-- TODO: 조건부 렌더링, 반복문 -->
    <h2>당신의 나이는 {{ age }}입니다.</h2>
    <p v-if="age > 39">당신은 어른입니다.</p>
    <p v-else-if="age > 13 && age <= 18">당신은 청소년입니다.</p>
    <p v-else>당신은 어른이 아닙니다.</p>

    <!-- 
      새롭게 생성해야 할 때는 v-if
      렌더링하는데 오래걸린다 하면 v-show 
    -->
    <h2 v-if="display">보입니다</h2>
    <h2 v-show="display">보입니다</h2>

    <p v-for="(animal, i) in animals" :key="i">{{ animal }}</p>

    <h4 v-for="(who, i) in person" :key="i">
      안녕하세요. {{ who.name }} 입니다. 직업은 {{ who.job }} 입니다.
      <p v-for="(item, j) in who.skill" :key="j">{{ item }}</p>
      <!-- <p>{{ who.skill }}</p> -->
    </h4>

    <template v-for="(animal, i) in animals" :key="i">
      <h2 v-if="animal !== 'rat'">{{ animal }}</h2>
    </template>

    <hr />

    <!-- TODO: 메소드, 이벤트 -->
    <div>
      <h1>{{ count }}</h1>
      <button @click="addNumber(1)">증가</button>
      <button @click="minusNumber">감소</button>
      <button @click="addNumber(10)">10증가</button>

      <h2>{{ hello }}</h2>
      <button @click="greeting">인사하기</button>
      <button @click="goodbye">작별하기</button>
      <br />
      <button @click="greeting($event, 10)">10더하기</button>
      <button @click="greeting($event, 100)">100더하기</button>

      <div @click="getMousePosition" class="box"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      animail: 'Monkey',
      food: 'banana',
      message: '<h2>이것은 수류탄이여</h2>',
      image: 'https://placeimg.com/100/100/any',
      age: 15,
      display: false,
      animals: ['monkey', 'rat', 'dog', 'lion'],
      person: [
        {
          name: 'chanCo',
          job: 'developer',
          gender: 'male',
          skill: ['html', 'css', 'js'],
        },
        { name: 'john', job: '백수', gender: 'male', skill: ['html', 'css', 'js'] },
        { name: 'lisa', job: 'pm', gender: 'female', skill: ['html', 'css', 'js'] },
      ],
      count: 0,
      hello: '',
    };
  },
  methods: {
    addNumber(value) {
      // 데이터에 접근하기 위해서는 this 사용해야함
      this.count += value;
    },
    // Arrow function을 사용하게 되면 렉시컬스코프가 된다
    // 고로 데이터를 찾지 못함
    minusNumber() {
      this.count--;
    },
    greeting(e, value) {
      // e.pageX
      this.hello = `마우스 좌표 ${e.pageX}와 더하기 ${value}는 ${e.pageX + value}이다.`;
    },
    goodbye() {
      this.hello = '잘가라';
    },
    getMousePosition(e) {
      console.log(e)
      this.hello = `마우스 위치는 가로 ${e.pageX}, 세로 ${e.pageY}`
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
  font-size: 30px;
}

.orange {
  color: orange;
}
.salmin {
  color: salmon;
}
.red {
  color: red;
}
.not-good {
  text-decoration: line-through;
}

button {
  width: 100px;
  height: 100px;
  font-size: 24px;
}

.box {
  width: 500px;
  height: 500px;
  background-color: aquamarine;
}
</style>
