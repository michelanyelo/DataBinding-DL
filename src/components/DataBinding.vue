<script>
export default {
    name: 'DataBinding',
    data() {
        return {
            backgroundBox: '',
            textColor: ''
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="selectores">
            <label for="backgroundBox">Color de fondo: </label>
            <input id="backgroundBox" type="text" v-model="backgroundBox">
            <label for="textColor">Color de texto: </label>
            <input id="textColor" type="text" v-model="textColor">
        </div>
        <div class="box" :style="{ backgroundColor: backgroundBox }">
            <p :style="{ color: textColor }">Awesome Vue.js</p>
        </div>
    </div>
</template>

<style>
.container {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 10px;
    width: 100%;
    max-width: 100%;
    margin: 0 auto;
}

.selectores,
.box {
    flex: 1;
    display: flex;
    flex-direction: column;
}

.selectores {
    justify-content: center;
}

.box {
    height: 100px;
    width: 100px;
    border: 1px;
}
</style>
