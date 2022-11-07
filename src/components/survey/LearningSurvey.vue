<template>
    <div>
        <base-card>
            <div id="git">
                <a href="https://github.com/sajwebsolutions/vue-feedback" target="_blank">View Code on GitHub</a>
            </div>
            <h2>How Was Your Learning Experience?</h2>
            <h5>A Feedback App with Back-end Technology</h5>
            <hr>
            <form @submit.prevent="submitSurvey">

                <div class="form-control">
                    <label for="name">Your Name</label>
                    <input type="text" id="name" name="name" v-model.trim="enteredName">
                </div>

                <h3>My Learning Experience Was:</h3>

                <div class="form-control">
                    <input type="radio" id="rating-poor" name="rating" value="poor" v-model="chooseRating">
                    <label for="rating-poor">Poor</label>
                </div>

                <div class="form-control">
                    <input type="radio" id="rating-average" name="rating" value="average" v-model="chooseRating">
                    <label for="rating-average">Average</label>
                </div>

                <div class="form-control">
                    <input type="radio" id="rating-great" name="rating" value="great" v-model="chooseRating">
                    <label for="rating-great">Great</label>
                </div>

                <br>
                <div class="form-control">
                    <base-button  mode="active_btn btn_large" type="submit" btnText="Submit"/>
                    <p v-if="invalidInput">
                        <span>Fill Complete Form</span>
                    </p>
                </div>

            </form>
        </base-card>
    </div>
</template>

<script>
    export default {
        //emits: ['survey-submit'],

        data() {
            return {
                enteredName: '',
                chooseRating: null,
                invalidInput: false
            }
        },

        methods:{
            submitSurvey()
            {
                if( this.enteredName    === '' || this.chooseRating === null )
                {
                    this.invalidInput = true;
                    return;
                }

                this.invalidInput = false;

                //Emit the function with form values
                /*this.$emit('survey-submit', {
                    username: this.enteredName,
                    rating: this.chooseRating
                });*/


                //Storing Data to Firebase.
                fetch('https://feedbackapp-6f659-default-rtdb.firebaseio.com/mysurveys.json', {
                    method: 'POST',
                    headers: {
                        'Content-Type' : 'application/json'
                    },
                    body: JSON.stringify({
                        name: this.enteredName,
                        rating: this.chooseRating
                    }),
                });

                //Default - Make fields empty
                this.enteredName = '';
                this.chooseRating = null;
            }
        }
    }
</script>


<style>

    #git{
        float: right;
    }

    form{
        margin-top: 3rem;
    }


    .form-control {
        margin: 0.5rem 0;
    }

    input[type='text'] {
        display: block;
        width: 20rem;
        margin-top: 0.5rem;
        padding: 5px;
    }

    p span{
        color: red;
        font-size: 12px;
    }
</style>