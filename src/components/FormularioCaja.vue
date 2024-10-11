<template>
    <div style="display: flex; gap: 20px; justify-content: center; font-family: monospace">
        <form id="formulario">
            <label>
                <h3>bgColor</h3>
                <input type="color" v-model="bgColor">
            </label>
            <label>
                <h3>textColor</h3>
                <input type="color" v-model="textColor">
            </label>

            <label>
                <h3> border radius</h3>
                <input v-model="borderRadiusValue" type="range" min="0" max="50">
            </label>

            <label>
                <h3>Contenido texto</h3>
                <textarea v-model="textContent"
                    placeholder="escribe aquí lo que quieras que aparezca en la caja del lado"></textarea>
            </label>
            <div class="checklabel">
                <h3>¿Mostrar texto?</h3>
                <input v-model="textCheck" type="checkbox">
            </div>
            <label>
                <h3>Fuente</h3>
                <select v-model="selectedFont">
                    <option v-for="( font, index ) in textFonts" :key="`font-${index}`" :value="font">{{ font }}
                    </option>
                </select>
            </label>
            <div class="checklabel">
                <h3>¿Opacidad?</h3>
                <input v-model="opacityCheck" type="checkbox" >
            </div>
            <label>
                <h3>Tamaño letra</h3>
                <div style="margin:10px 40px">
                    <label for="fs-pequeno">
                        Pequeño <input v-model="fsize" type="radio" value="15px" name="fsize" id="fs-pequeno">
                    </label>
                    <label for="fs-mediano">
                        Mediano <input v-model="fsize" type="radio" value="25px" name="fsize" id="fs-mediano">
                    </label>
                    <label for="fs-grande">
                        Grande <input v-model="fsize" type="radio" value="35px" name="fsize" id="fs-grande">
                    </label>
                </div>
            </label>

        </form>
        <article id="caja" :style="{
            backgroundColor: bgColor,
            color: textColor,
            borderRadius: `${borderRadiusValue}%`,
            fontFamily: selectedFont,
            opacity: opacityCheck ? 0.5 : 1,
            fontSize: fsize
        }">
            <h2 v-if="textCheck">{{ textContent }}</h2>
        </article>
    </div>

</template>

<script>
export default {
    name: 'MiComponente',
    data() {
        return {
            borderRadiusValue: 0,
            bgColor: '#333',
            textColor: '#eee',
            textContent: 'Awesome Vue',
            textCheck: true,
            textFonts: ['monospace', 'cursive', 'fantasy'],
            selectedFont: 'fantasy',
            opacityCheck: false,
            fsize: '20px'
        };
    },
};
</script>

<style scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}

#formulario {
    background-color: #1a0;
    display: flex;
    flex-direction: column;
    color: #eee;
    width: 500px;
    padding:20px 10px;
    gap: 20px
}

#formulario > label {
    margin: 0 auto;
    width: 80%;
    display: flex;
    flex-direction: column;
    padding: 10px;
    text-align: center
}


select {
    width: 100%;
}

textarea {
    width: 100%;
}

#formulario>label>input {
    width: 100%;
    display: flex;
    flex-direction: row;
}

.checklabel{
    display: flex;
    justify-content: center;
    gap: 20px;
}



#caja {
    height: 400px;
    width: 400px;
    border: #aaa solid 5px;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
