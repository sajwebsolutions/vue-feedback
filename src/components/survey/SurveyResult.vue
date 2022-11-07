<template>
    <div>
        <ul>
            <li>
                <h3>{{ name }}</h3>
                <p>
                    <span :class="ratingClass">{{ rating }}</span>
                </p>
            </li>
        </ul>
    </div>
</template>


<script>
    export default {

        props: ['name', 'rating'],

        computed: {
            ratingClass()
            {
                return 'rating--' + this.rating;
            }
        }
    }
</script>

<style scoped>
    li{
        background-color: beige;
        list-style: none;
        padding: 4px 16px;
        margin-bottom: 15px;
    }

    .rating--poor {
        color: #b80056;
    }

    .rating--average {
        color: #330075;
    }

    .rating--great {
        color: #008327;
    }
</style>