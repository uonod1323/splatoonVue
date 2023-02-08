<template>
  <div class = "container">
    <div class="content-container">
      <p>폰트 테스트용1</p>
    </div>
  </div>
</template>
  
  <script>
  export default {
    name: 'MainPage',
    data(){
      return {
        questions : [
          {
            question : "어떤 사냥꾼이 사냥을 하기 위해 동료와 사냥감을 찾아 나섭니다. 그리고 눈 앞에서 사냥감과 마주쳤습니다. 그 사냥감은 무엇인가요?",
            answer1   : "호랑이",
            answer2   : "늑대",
            answer3   : "사슴",
            answer4   : "동료 사냥꾼을 사냥감으로 착각한 것이었다"
          },
          {
            question : "어떤 사냥꾼이 사냥을 하기 위해 동료와 사냥감을 찾아 나섭니다. 그리고 눈 앞에서 사냥감과 마주쳤습니다. 그 사냥감은 무엇인가요?",
            answer1   : "호랑이",
            answer2   : "늑대",
            answer3   : "사슴",
            answer4   : "동료 사냥꾼을 사냥감으로 착각한 것이었다"
          }
        ]
      }
    }
  }
  </script>
  
  <style>
    body {
        background-image: url("../assets/splatoon3-pattern-01-3840x2160-1.jpg");
        background-size: cover;
        background-repeat: no-repeat;
        background-attachment: fixed;
    }
    .content-container {
      background-color: rgba(255, 255, 255, 0.3);
      border-radius: 20px;
      width: 800px;
      height: 90vh;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    @font-face {
      font-family: 'spla2k';
      src: url('../assets/fonts/스플래2K.ttf') format('woff');
    }
    @font-face {
      font-family: 'SplatoonKVer2.0';
      src: url('../assets/fonts/SplatoonKVer.2.0.ttf') format('woff');
    }
    p {
      font-family: 'spla2k';
    }   
  </style>
  