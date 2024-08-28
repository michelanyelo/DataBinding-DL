<script>
export default {
    name: 'DataBinding',
    data() {
        return {
            backgroundBox: '',          // Color de fondo del cuadro
            textColor: '',               // Color del texto
            showTexto: false,            // Controla la visibilidad del texto
            borderBox: '0',              // Grosor del borde del cuadro
            borderRadiusBox: '0',        // Radio de borde del cuadro
            borderColor: '',             // Color del borde del cuadro
            textContent: '',             // Contenido textual
            typoStyle: '',               // Estilo de tipografía seleccionada
            fontStyle: ['normal', 'italic', 'oblique'], // Opciones de estilos de tipografía
            opacityBox: false,           // Controla la opacidad del cuadro
            selectedFontSize: 16,        // Tamaño de fuente seleccionado
            sizeFont: [                  // Opciones de tamaño de fuente
                { value: 10, label: 'Pequeño (10px)' },
                { value: 16, label: 'Mediano (16px)' },
                { value: 32, label: 'Grande (32px)' },
                { value: 64, label: 'Extra Grande (64px)' }
            ]
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="selectores">
            <label for="backgroundBoxInput">Color de fondo: </label>
            <input id="backgroundBoxInput" type="text" v-model="backgroundBox" class="input-field">

            <label for="mostrarTextCheck">Mostrar texto: </label>
            <input id="mostrarTextCheck" type="checkbox" v-model="showTexto">

            <label for="textContentInput">Contenido Textual: </label>
            <input id="textContentInput" type="text" v-model="textContent" class="input-field">

            <label for="textColorInput">Color de texto: </label>
            <input id="textColorInput" type="text" v-model="textColor" class="input-field">

            <label for="typoTextSelect">Tipografía: </label>
            <select id="typoTextSelect" v-model="typoStyle" class="input-select">
                <option v-for="(style, idx) in fontStyle" :key="idx" :value="style">{{ style }}</option>
            </select>

            <label for="fontSize">Tamaño de letra: </label>
            <div id="fontSize" class="font-size-options">
                <div v-for="(size, idx) in sizeFont" :key="idx">
                    <input type="radio" :id="'fontSize' + idx" :value="size.value" v-model="selectedFontSize">
                    <label :for="'fontSize' + idx">{{ size.label }}</label>
                </div>
            </div>

            <label for="borderColorInput">Color de borde: </label>
            <input id="borderColorInput" type="text" v-model="borderColor" class="input-field">

            <label for="borderTextRange">Borde: </label>
            <input id="borderTextRange" type="range" min="0" max="30" v-model="borderBox" class="input-range">

            <label for="borderRadiusRange">Borde redondeado: </label>
            <input id="borderRadiusRange" type="range" min="0" max="50" v-model="borderRadiusBox" class="input-range">

            <label for="opacityBoxCheck">Opaco: </label>
            <input id="opacityBoxCheck" type="checkbox" v-model="opacityBox">
        </div>

        <!-- Cuadro dinámico -->
        <div :class="{ 'box-block': backgroundBox }" v-show="backgroundBox"
            :style="{ backgroundColor: backgroundBox, border: borderBox + 'px solid', borderRadius: borderRadiusBox + '%', borderColor: borderColor, opacity: opacityBox ? 1 : 0.5 }">
            <p :style="{ color: textColor, fontStyle: typoStyle, fontSize: selectedFontSize + 'px' }"
                v-show="showTexto">{{ textContent }}</p>
        </div>
    </div>
</template>

<style>
/* Diseño general del contenedor */
.container {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    gap: 15px;
    width: 100%;
    max-width: 100%;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10px;
    background-color: #f9f9f9;
}

/* Estilos para las columnas */
.selectores,
.box {
    flex: 1;
    display: flex;
    flex-direction: column;
}

.selectores {
    justify-content: center;
}

/* Estilo para el cuadro cuando tiene un color de fondo */
.box-block {
    width: 400px;
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
}

/* Estilos para los campos de entrada */
.input-field {
    margin-bottom: 10px;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.input-range {
    margin-bottom: 10px;
}

.input-select {
    margin-bottom: 10px;
    padding: 5px;
    border-radius: 5px;
}

/* Opciones de tamaño de fuente */
.font-size-options {
    margin-bottom: 10px;
    display: flex;
    flex-direction: column;
}

/* Caja de opacidad */
.opacityBox {
    opacity: 0.5;
}
</style>
