<template>
    <div>
        <button :class="mode" :type="type">{{ btnText }}</button>
    </div>
</template>

<script>
    export default {
        props: ['mode', 'type', 'btnText'],
    }
</script>

<style scoped>
    .active_btn{
        background-color: blueviolet;
        padding: 5px;
        cursor: pointer;
        color: white;
        border: 2px solid black;
    }

    .active_btn:hover{
        background-color: darkslateblue;
    }

    .btn_large{
        width: 100%;
        padding: 10px;
    }
</style>