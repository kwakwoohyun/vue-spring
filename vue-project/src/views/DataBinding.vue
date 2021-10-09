<template>
  <h1>1. 문자열 데이터 바인딩</h1>
  <h3>Hello, {{ title }}</h3>
  <hr />
  <h1>2. HTML 데이터 바인딩</h1>
  <div>{{ htmlString }}</div>
  <div v-html="htmlString"></div>
  <hr />
  <h1>3. Form 입력 데이터 바인딩</h1>
  <h2>Input type=text</h2>
  <input type="text" v-model="valueModel" name id />
  <h2>Input type=number</h2>
  <input type="number" v-model.number="numberModel" name id />
  <h2>Textarea</h2>
  <textarea v-model="message" name id cols="30" rows="10"></textarea>
  <h2>Select</h2>
  <select v-model="city" name id>
    <option value="02">서울</option>
    <option value="21">부산</option>
    <option value="064">제주도</option>
  </select>
  <h2>Input type=checkbox</h2>
  <label>
    <input type="checkbox" v-model="checked" name id />
    {{ checked }}
  </label>
  <label>
    <input type="checkbox" v-model="checked2" true-value="yes" false-value="no" name id />
    {{ checked2 }}
  </label>
  <br />
  <label>
    <input type="checkbox" v-model="checked3" value="서울" name id />
    서울
  </label>
  <label>
    <input type="checkbox" v-model="checked3" value="부산" name id />
    부산
  </label>
  <label>
    <input type="checkbox" v-model="checked3" value="제주" name id />
    제주
  </label>
  <br />
  <span>체크한 지역 : {{ checked3 }}</span>
  <h2>Radio</h2>
  <label>
    <input type="radio" v-bind:value="radioValue1" v-model="picked" name id />
    서울
  </label>
  <label>
    <input type="radio" v-bind:value="radioValue2" v-model="picked" name id />
    부산
  </label>
  <label>
    <input type="radio" v-bind:value="radioValue3" v-model="picked" name id />
    제주
  </label>
  <br />
  <span>선택한 지역 : {{ picked }}</span>
  <hr />
  <h1>4. 속성 (Attribute) 바인딩</h1>
  <h2>Img 객체의 src</h2>
  <img v-bind:src="imgSrc" alt />
  <h2>button 객체의 disabled</h2>
  <input type="text" v-model="textValue" />
  <button type="button" v-bind:disabled="textValue==''">Click</button>
  <hr />
  <h1>5. 클래스 바인딩</h1>
  <div
    class="container"
    v-bind:class="{
    'active': isActive, 'text-red': hasError
    }"
  >Class Binding</div>
  <div class="container" v-bind:class="[activeClass, errorClass]">Class Binding</div>
  <hr />
  <h1>6. 인라인 스타일 바인딩</h1>
  <div v-bind:style="styleObject">인스인 스타일 바인딩</div>
</template>
<script>
export default {
  data() {
    return {
      title: "World",
      htmlString: '<p style="color:red;">This is a red string.</p>',
      valueModel: "South Korea",
      numberModel: 3,
      message: "여러 줄을 입력할 수 있는 textarea 입니다.",
      city: "064",
      checked: true,
      checked2: true,
      checked3: [],
      picked: "",
      radioValue1: "서울",
      radioValue2: "부산",
      radioValue3: "제주",
      imgSrc: "https://kr.vuejs.org/images/logo.png",
      textValue: "",
      isActive: true,
      hasError: false,
      activeClass: "active",
      errorClass: "text-red",
      styleObject: {
        color: "red",
        fontSize: "20px"
      }
    };
  }
};
</script>
<style scoped>
container {
  width: 100%;
  height: 200px;
}
.active {
  background-color: yellow;
  font-weight: bold;
}
.text-red {
  color: red;
}
</style>