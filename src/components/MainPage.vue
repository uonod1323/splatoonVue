<template>
  <div class = "container">
    <div class="content-container">
      <div class="question-container">
        <p v-html="question"></p>
      </div>
      <div class="flex-container">
        <div class="flex-item" @click="saveAnswer(1)"><p v-html="answer1"></p></div>
        <div class="flex-item" @click="saveAnswer(2)"><p v-html="answer2"></p></div>
        <div class="flex-item" @click="saveAnswer(3)" v-if="answer3 != '' "><p v-html="answer3"></p></div>
        <div class="flex-item" @click="saveAnswer(4)" v-if="answer4 != '' "><p v-html="answer4"></p></div>
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
        style2       : '',      // 무기군 쪼개기를 위한 상세분류
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
            question     : "집을 짓는 목수가 2층으로 올라가려고 합니다. \n 그런데 계단이 망가져 있었습니다. \n 목수는 어떻게 행동할까요?",
            answer1      : "급한 대로 근처에 쌓여 있는 \n 자재들을 밟고 올라간다.",
            answer2      : "다른 사람들과 함께 \n 계단을 먼저 고친다.",
            answer3      : "",
            answer4      : ""
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
              this.position = "close"; //근거리
              break; 
            case 2:
              this.position = "close-mid"; //근중거리
              break;
            case 3:
              this.position = "mid"; //중간
              break;
            case 4:
              this.position = "far"; //원거리
              break; 
          }
          this.questionType = "style";
          this.setQuestion(this.questionType);
        }else if(this.questionType === "style"){
          switch(answer){
            case 1: 
              this.style = "target";    //목표지향
              break; 
            case 2:
              this.style = "cooperative";  //협력적인
              break;
          }

          // 바로 플레이어의 성향을 도출하거나, 세번째 질문으로 넘어가거나.
          // 성향 도출은 함수를 만들어서 공통으로 처리할 수 있도록 합니다. 여기서는 if문만 가지고 처리.
          if(this.position === "mid"){

            if(this.style === "target"){
              this.weaponType = "slosher"
              console.log("넌슬딱");
              this.$emit('changeCurrentPage', this.weaponType) //부모로 데이터 전달.
            }
            else{
              this.weaponType = "shooter"
              console.log("넌슈딱");
              this.$emit('changeCurrentPage', this.weaponType)
            }
          }else{
            this.questionType = "style2";
            this.setQuestion(this.questionType);
          }
        }
      }


    }
  }
  </script>
  
  <style>
   
  </style>
  