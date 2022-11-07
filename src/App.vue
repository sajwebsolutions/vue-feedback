<template>
  <header-comp/>
  <learning-survey/>
  <user-experiences/>
</template>

<script>

  import LearningSurvey from "./components/survey/LearningSurvey";
  import UserExperiences from "./components/survey/UserExperiences"
  import HeaderComp from "./components/UI/HeaderComp";

  export default {

    components: {
      LearningSurvey,
      UserExperiences,
      HeaderComp
    },

    /*data() {
      return {
        savedSurveyResult: []
      }
    },*/

    /*methods:{
      storeData(surveyData)
      {
        const surveyResult  = {
          name: surveyData.username,
          rating: surveyData.rating,
          id: new Date().toISOString()
        };

        this.savedSurveyResult.push(surveyResult);
        console.log(surveyResult);

      }
    }*/

  }
</script>


<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed&display=swap');

  body{
    font-family: "Roboto Condensed";
    margin: 0 auto;
  }
</style>