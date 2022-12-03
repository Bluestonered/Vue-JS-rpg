<template>
    <div>
        <v-row class="center" v-for="(title, index) in titles" :key="index">

            <button>
                <a :href=title.path >
                    <span class="button_top"> {{title.text}}
                    </span>
                </a>
            </button>

        </v-row>

    </div>
</template>
  
<script>
export default {
    name: 'NavBar',
    props: { titles: Array }
}
</script>

<style scoped>
.center {
    align-content: center;
    justify-content: center;
}

a {
    text-decoration: none; 
}
button {
    /* Variables */
    --button_radius: 0.85em;
    --button_color: #e8e8e8;
    --button_outline_color: #000000;
    font-size: 17px;
    font-weight: 0px;
    border: none;
    border-radius: var(--button_radius);
    background: var(--button_outline_color);
    margin: 5px 0;
    padding: 0px;
    width: 90%;
}

.button_top {
    display: block;
    box-sizing: border-box;
    border: 2px solid var(--button_outline_color);
    border-radius: var(--button_radius);
    padding: 0.75em 1.5em;
    background: var(--button_color);
    color: var(--button_outline_color);
    transform: translateY(-0.2em);
    transition: transform 0.1s ease;
}

button:hover .button_top {
    /* Pull the button upwards when hovered */
    transform: translateY(-0.33em);
}

button:active .button_top {
    /* Push the button downwards when pressed */
    transform: translateY(0);
}
</style>