<template>
    <p>Message de depart</p>
</template>

<script>
export default {

}
</script>

<style>
.start {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
.start::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    opacity: 0.6;
    background-image: url(../assets/nuage_bleu.png), url(../assets/nuage_bleu3.png), url(../assets/nuage_rose.png), url(../assets/nuage_rose2.png);
    background-repeat: no-repeat, no-repeat;
    background-position:
        -100px -100px,
        calc(100% + 50px) calc(100% + 50px),
        -50px calc(100% + 50px),
        calc(100% + 50px) -50px; 
    animation: 1000ms 400ms show both;
}

@keyframes show {
    from {
        opacity: 0;
    }
    to {
        opacity: 0.6;
    }
}
</style>