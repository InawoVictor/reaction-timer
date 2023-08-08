<template>
    <div class="result">
        <p>Reaction time - {{score}}ms</p>
        <p class="rank">{{rank}}</p>
    </div>

</template>

<script>

export default {
    name: "Result",
    props: ['score'],
    data() {
        return{
            rank: null
        }
    },
    mounted() {
        if(this.score < 250){
            this.rank = " Ninja reflexes"
        } else if (this.score < 350) {
            this.rank = "Rapid reflexes"
        } else {
            this.rank = "Snail pace..."
        }
    },
}
</script>

<style>
    .result{
        width: 400px;
        border-radius: 20px;
        background: teal;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
    .rank {
        font-size: 1.4em;
        font-weight: bold;
    }
</style>