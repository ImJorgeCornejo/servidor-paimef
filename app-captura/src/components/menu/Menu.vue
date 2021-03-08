<template>
    <div class="menuPrincipal">
        <BarraMenu></BarraMenu>
        <Menucontenedor></Menucontenedor>
    </div>
    <router-view/>
</template>

<script>

import BarraMenu from '../menu/Barramenu.vue';
import Menucontenedor from '@/components/menu/Menucontenedor.vue';

export default {
    components: {
        BarraMenu,
        Menucontenedor
    }    
}
</script>

<style scoped>
    .menuPrincipal{
        width:100%;
    }
</style>