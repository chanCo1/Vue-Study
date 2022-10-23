<template>
  <div>
    <!-- TODO: 데이터 바인딩 -->
    <div>Hello {{ userName }}</div>
    <h1 class="title">This is Title.</h1>
    <h2 :class="dynamic">??</h2>
    <img :src="image.src" :alt="image.alt" />
    <hr />

    <!-- TODO: CSS클래스 -->
    <h2 :class="isDone ? 'line-through' : 'highlight'">line-through</h2>
    <h2 :class="textDecoration">line-through</h2>
    <p :class="{ highlight: isDone, 'text-red': userName === 'chanCo' }">
      요요
    </p>
    <p :class="['content', userName === 'chanCo' ? 'green' : 'line-through']">
      ㅋㅋㅋㅋㅋㅋ
    </p>
    <hr />

    <!-- TODO: 조건부 렌더링 -->
    <h2 v-once v-text="user.name"></h2>
    <h2 v-text="user.name"></h2>
    <input type="text" v-model="user.name" />

    <p v-if="user.name === 'chanCo'">{{ user.job }}</p>
    <p v-else>이름을 보여줄 수 없다</p>

    <p v-if="showName">{{ user.name }} IF</p>
    <p v-show="showName">
      {{ user.name }} 이건 css를 건들여서 display: none 처리를 함
    </p>

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
  <hr />

  <!-- TODO: 리스트 렌더링 -->
  <p>{{ fruits }}</p>
  <ul>
    <li v-for="(fruit, i) in fruits" :key="i">{{ fruit }}</li>
  </ul>

  <h2 v-for="(value, key, i) in user" :key="i">
    {{ key }} // {{ value }} , {{ i }}
  </h2>

  <p v-for="n in 10" :key="n">{{ n }}</p>

  <div v-for="(animal, i) in animals" :key="i">
    <h2>{{ animal.name }}</h2>
    <p>{{ animal.size }}</p>
    <ul>
      <li v-for="(food, i) in animal.food" :key="i">{{ food }}</li>
    </ul>
  </div>

  <div>
    <ul>
      <li
        v-for="(city, i) in cities.filter((c) => c.province === '경상도')"
        :key="i"
      >
        {{ city.name }}
      </li>
      <br />
      <li v-for="(city, i) in cities" :key="i">
        <span v-if="city.province === '경상도'">{{ city.name }}</span>
      </li>
      <br />
      <template v-for="(city, i) in cities" :key="i">
        <li v-if="city.province === '경기도'">{{ city.name }}</li>
      </template>
    </ul>
  </div>

  <!-- TODO: 메서드 -->
  <p>더하기 10 >> {{ add(10) }}</p>
  <p>동갑의 10명이 있다면 나의 총 합은 {{ multiply(user.age) }}</p>
  <p>{{ getTotalScore(100) }}</p>

  <!-- TODO: 이벤트 -->
  <h3>HAHAHAHA {{ userName }}</h3>
  <button @click.middle="changeName">change name</button>
  <button @mouseover="userName = '요요요'" @mouseleave="userName = '베벱베ㅔ'">
    change name
  </button>
  <br />
  <a @click.prevent="movePage" href="https://www.naver.com">naver</a>

  <h4>{{ number }}</h4>
  <button @click="increase($event, 1)">1증가</button>
  <hr />

  <!-- TODO: FORM 핸들링 -->
  <div>
    {{ user }}
    <form action="">
      <div>
        <label for="name">이름</label>
        <input type="text" id="name" @input="setValue" />
        <h2>{{ user.name }}</h2>
      </div>

      <div>
        <label for="city">사는 곳</label>
        <select name="" id="city" v-model="user.city">
          <option value="">선택하세요</option>
          <option value="seoul">서울</option>
          <option value="daejeon">대전</option>
          <option value="daegu">대구</option>
          <option value="busan">부산</option>
          <option value="gwangju">광주</option>
        </select>
      </div>

      <div>
        <label for="food">좋아하는 음식</label>
        <select name="" id="food" v-model="user.favorite" multiple>
          <option
            v-for="(option, i) in foodOptions"
            :key="i"
            :value="option.code"
          >
            {{ option.label }}
          </option>
        </select>
      </div>

      <div>
        <label for="job">직업</label>
        <input
          type="checkbox"
          value="programmer"
          v-model="user.job2"
        />프로그래머
        <input type="checkbox" value="singer" v-model="user.job2" />가수
        <input type="checkbox" value="teacher" v-model="user.job2" />선생님
      </div>

      <div>
        <label for="gender">성별</label>
        남<input type="radio" value="male" v-model="user.gender" /> 여<input
          type="radio"
          value="female"
          v-model="user.gender"
        />
      </div>
    </form>
  </div>
  <hr />

  <!-- TODO: Directives -->
  <h2>유저 이름은 {{ userName }}</h2>
  <button @click="changeName">이름변경</button>
  <!-- v-pre => 컴파일에서 제외, 그대로 출력 -->
  <h3 v-pre>{{ userName }}</h3>

  <input v-focus type="text" />
  highlight => <input v-highlight type="text" />
  <hr />

  <!-- TODO: Computed -->
  <h2>{{ address }}</h2>
  <h2>computed >> 내가 받은 점수: {{ totalScore }}</h2>
  <h2>method >> 내가 받은 점수: {{ getTotalScore2() }}</h2>
  <hr />

  <!-- TODO: Watch -->
  <h2>current Money :: {{ money }}</h2>
  <button @click="money += 100">earn money</button>
  <button @click="money -= 100">spend money</button>

  <h2>{{ receit }}</h2>
  <button @click="receit.food += 500">earn money</button>
  <br />

  <input type="text" v-model="userName" />
  <hr />

  <!-- TODO: component -->
  <GreetingUser
    :userName="userName"
    :visitCount="visitCount"
    :siteInfo="siteInfo"
  />
  <!-- <GreetingUser userName="dooli" />
  <GreetingUser userName="pororo" />
  <GreetingUser /> -->
  <button @click="changeName()">change</button>

  <ProductList :products="products" />

  <button @click="displayDetail = true">show detail</button>
  <DetailView
    v-if="displayDetail"
    :displayDetail="displayDetail"
    @closeDetail="close"
    @sendData="showData"
  />

  <CompLevel1 />

  <button @click="activeTab = 'Menu1'">menu1</button>
  <button @click="activeTab = 'Menu2'">menu2</button>
  <button @click="activeTab = 'Menu3'">menu3</button>

  <!-- <Menu1 v-if="activeTab === 'Menu1'" />
  <Menu2 v-if="activeTab === 'Menu2'" />
  <Menu3 v-if="activeTab === 'Menu3'" /> -->
  <keep-alive>
    <component :is="activeTab"></component>
  </keep-alive>

  <!-- slot -->
  <CardView>
    <template v-slot:header>
      <h3>Random Image</h3>
    </template>
    <template v-slot:body>
      <img src="https://placeimg.com/100/100/any" alt="" />
    </template>
    <template v-slot:footer>
      <small>Thank u</small>
    </template>
  </CardView>
  <!-- <CardView>
    <img src="https://placeimg.com/100/100/any" alt="" />
  </CardView>
  <CardView>
    <ul>
      <li>짬뽕</li>
      <li>짜장</li>
    </ul>
  </CardView>
  <CardView></CardView> -->
</template>

<!-- JS -->
<script>
import GreetingUser from './components/GreetingUser.vue';
import ProductList from './components/ProductList.vue';
import DetailView from './components/DetailView.vue';
import CompLevel1 from './components/provide-inject/CompLevel1.vue';
import Menu1 from './components/tabItems/Menu1.vue';
import Menu2 from './components/tabItems/Menu2.vue';
import Menu3 from './components/tabItems/Menu3.vue';
import CardView from './components/slot/CardView.vue';

export default {
  name: 'App',

  /**
   * @component
   */
  components: {
    GreetingUser,
    ProductList,
    DetailView,
    CompLevel1,
    Menu1,
    Menu2,
    Menu3,
    CardView
  },

  /**
   * @data
   */
  data() {
    return {
      receit: {
        food: 3000,
        fee: 2000,
        fare: 10000
      },
      money: 0,
      userName: 'chanCo',
      number: 0,
      dynamic: 'content',
      image: {
        src: 'https://placeimg.com/200/200/any',
        alt: 'randome image'
      },
      textDecoration: 'line-through',
      isDone: true,
      user: {
        name: 'chanCo',
        age: 0,
        job: 'developer',
        job2: [],
        city: 'seoul',
        favorite: []
      },
      showName: true,
      question: 'frontend',
      fruits: ['banana', 'strawberry', 'apple', 'melon'],
      animals: [
        { name: 'hama', size: 'big', food: ['human', 'watermelon'] },
        { name: 'pig', size: 'medium', food: ['grass', 'pizza'] },
        { name: 'bird', size: 'small', food: ['ant', 'leaf'] }
      ],
      cities: [
        { name: '서울', province: '경기도' },
        { name: '대전', province: '충청도' },
        { name: '대구', province: '경상도' },
        { name: '부산', province: '경상도' },
        { name: '인천', province: '경기도' },
        { name: '광주', province: '전라도' }
      ],
      foodOptions: [
        { label: '자장면', code: 'J' },
        { label: '짬뽕', code: 'JB' },
        { label: '탕수육', code: 'TS' }
      ],
      address1: '성남시',
      address2: '분당구',
      address3: '정자동',
      grade: {
        math: 70,
        kor: 90,
        eng: 50,
        sci: 55
      },
      visitCount: 25,
      siteInfo: {
        name: 'Vue World',
        teacher: 'chanCo',
        subject: 'Front-End'
      },
      products: [
        { id: 0, name: 'TV', price: 500000, company: 'LG' },
        { id: 1, name: '전자레인지', price: 200000, company: '삼성' },
        { id: 2, name: '가스오븐', price: 300000, company: '한화' },
        { id: 3, name: '냉장고', price: 50000, company: '대우' },
        { id: 4, name: '에어컨', price: 100000, company: '해태' }
      ],
      displayDetail: false,
      activeTab: 'Menu1'
    };
  },

  /**
   * methods
   */
  methods: {
    add(num) {
      return this.user.age + num;
    },
    multiply(num1, num2 = 10) {
      return num1 * num2;
    },
    getTotalScore(num) {
      return this.multiply(num, num);
    },
    changeName() {
      this.userName = '퓡신';
    },
    movePage() {
      confirm('페이지 이동?') ? console.log('이동') : console.log('안함');
    },
    increase(e, num) {
      e.preventDefault();
      this.number += num;
    },
    setValue(e) {
      this.user.name = e.target.value;
    },
    getTotalScore2() {
      const { math, eng, kor, sci } = this.grade;
      return math + eng + kor + sci;
    },
    close() {
      this.displayDetail = false;
    },
    showData(data) {
      console.log(data);
    }
  },

  /**
   * directives
   */
  directives: {
    focus: {
      mounted(el) {
        el.focus();
      }
    },
    highlight: {
      mounted(el) {
        el.onclick = () => {
          el.style.background = 'salmon';
          el.style.color = '#fff';
        };
      }
    }
  },
  /**
   * @description method와 computed의 차이
   * - computed는 도출한 값이 캐시가 된다
   * - method는 값의 변화가 있을 때 마다 계속 실행된다
   */
  computed: {
    address() {
      return `${this.address1}/ ${this.address2}/ ${this.address3}`;
    },
    totalScore() {
      const { math, eng, kor, sci } = this.grade;
      return math + eng + kor + sci;
    }
  },

  /**
   * watch
   */
  watch: {
    userName: {
      handler(newValue) {
        console.log(newValue);
      },
      immediate: true
    },
    money(newValue, oldValue) {
      if (newValue > 1000 && newValue > oldValue) console.log('done');
      if (oldValue < 500 && newValue < oldValue) console.log('save money');
    },
    receit: {
      // console.log('변함', newValue, oldValue);
      handler(newValue) {
        console.log(newValue);
      },
      deep: true
    }
  },

  provide() {
    return {
      name: this.userName
    };
  }
};
</script>

<!-- Style -->
<style>
.title {
  /* color: red;
  background-color: yellow; */
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
