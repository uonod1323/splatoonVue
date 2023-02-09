<template>
  <div class = "container">
    <div class="content-container">
      <div class="question-container">
        <p v-html="question"></p>
      </div>
      <div class="flex-container">
        <div class="flex-item" @click="saveAnswer(1)" v-html="answer1"></div>
        <div class="flex-item" @click="saveAnswer(2)" v-html="answer2"></div>
        <div class="flex-item" @click="saveAnswer(3)" v-html="answer3"></div>
        <div class="flex-item" @click="saveAnswer(4)" v-html="answer4"></div>
      </div>
    </div>
  </div>
</template>
  
  <script>
  export default {
    name: 'MainPage',
    data(){
      return {
        questionType : '',       // 질문 타입
        position     : '',      // 근거리, 근중거리, 중거리, 원거리
        style        : '',      // 목표, 협력
        weaponType   : '',      // 무기군

        question     : '',      // 현재 질문
        answer1      : '',      // 답변 1
        answer2      : '',      // 답변 2
        answer3      : '',      // 답변 3
        answer4      : '',      // 답변 4

        questions : [
          {
            questionType : "position",
            question     : "사냥꾼이 동료와 사냥을 나갔습니다. \n 그리고 눈 앞에서 사냥감과 마주쳤습니다. \n 그 사냥감은 무엇인가요?",
            answer1      : "호랑이",
            answer2      : "늑대",
            answer3      : "사슴",
            answer4      : "동료 사냥꾼을 사냥감으로 \n 착각한 것이었다"
          },
          {
            questionType : "style",
            question     : "사냥꾼이 동료와 사냥을 나갔습니다. \n 그리고 눈 앞에서 사냥감과 마주쳤습니다. \n 그 사냥감은 무엇인가요?",
            answer1      : "호랑이",
            answer2      : "늑대",
            answer3      : "사슴",
            answer4      : "동료 사냥꾼을 사냥감으로 착각한 것이었다"
          },
        ]
      }
    },

    mounted(){
      this.questionType = "position";
      this.setQuestion(this.questionType);
    },

    methods : {
      setQuestion(QT){
        for(let i=0; i<this.questions.length; i++){
          if(this.questions[i].questionType === QT){
            this.question = this.questions[i].question.replace(/(?:\r\n|\r|\n)/g, '<br />');
            this.answer1 = this.questions[i].answer1.replace(/(?:\r\n|\r|\n)/g, '<br />');
            this.answer2 = this.questions[i].answer2.replace(/(?:\r\n|\r|\n)/g, '<br />');
            this.answer3 = this.questions[i].answer3.replace(/(?:\r\n|\r|\n)/g, '<br />');
            this.answer4 = this.questions[i].answer4.replace(/(?:\r\n|\r|\n)/g, '<br />');
          }
        }
      },

      saveAnswer(answer){
        if(this.questionType === "position"){
          switch(answer){
            case 1: 
              this.position = "close";
              break; 
            case 2:
              this.position = "close-mid";
              break;
            case 3:
              this.position = "mid";
              break;
            case 4:
              this.position = "far";
              break; 
          }
          this.questionType = "style";
          this.setQuestion(this.questionType);
        }
      }


    }
  }
  </script>
  
  <style>
    div {
      font-family: 'spla2k';
      color: white;
    }
    body {     
        background-image: url("../assets/splatoon3-pattern-01-3840x2160-1.jpg");
        background-size: cover;
        background-repeat: no-repeat;
        background-attachment: fixed;
    }
    .content-container {
      background-color: rgba(255, 255, 255, 0.3);
      border-radius: 20px;
      width: 650px;
      padding : 50px;
      height: 90vh;
      margin: 0 auto;
      align-items: center;
      justify-content: center;
    }
    .question-container {
      background-color : rgb(0, 0, 0);
      font-size: 40px;
      border-radius: 50px;
      padding : 5px;
    }
    @font-face {
      font-family: 'spla2k';
      src: url('../assets/fonts/스플래2K.ttf') format('woff');
    }
    @font-face {
      font-family: 'SplatoonKVer2.0';
      src: url('../assets/fonts/SplatoonKVer.2.0.ttf') format('woff');
    }
    .flex-container{
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: repeat(2, 1fr);
      grid-gap: 10px;
    }
    .flex-item {
        width:300px;
        height:200px;
        font-size: 30px;
        background-color: grey;
        border-radius: 30px;
        margin: 5px;
        text-align: center;
    }
  </style>
  