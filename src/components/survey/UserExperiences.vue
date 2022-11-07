<template>
    <div>
        <base-card>
            <h2>User Feedback</h2>
            <hr>
            <p v-if="isLoading">
                Loading...
            </p>
            <div v-else-if="!isLoading && (!results || results.length === 0)">
                <p>No Feedback Found</p>
            </div>
            <div v-else-if="!isLoading && (!results || results.length > 0)">
                <survey-result
                        v-for="result in results"
                        :key="result.id"
                        :name="result.name"
                        :rating="result.rating"
                />
            </div>

            <div>
                <br>
                <br>
                <base-button mode="active_btn btn_large" type="button" btnText="Load User Feedback" @click="loadfeedback"/>
            </div>
        </base-card>
    </div>
</template>

<script>

    import SurveyResult from "./SurveyResult";

    export default {

        components: {
            SurveyResult
        },

        //props: ['results'],

        data() {
            return {
                results: [],
                isLoading: true
            }
        },

        methods:{
            loadfeedback()
            {
                //Fetching The Data From Firebase.
                fetch('https://feedbackapp-6f659-default-rtdb.firebaseio.com/mysurveys.json').then((response) => {
                  if( response.ok )
                  {
                      return response.json();
                  }
                }).then((data) => {

                    this.isLoading = false;
                    const results   =   [];

                    for( const id in data )
                    {
                        results.push({
                            id: id,
                            name: data[id].name,
                            rating: data[id].rating
                        });
                    }

                    this.results = results
                });
            },
        },

        mounted() {
            this.loadfeedback();
        }
    }
</script>