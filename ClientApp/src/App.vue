<template>
  <div id='app' class='b-container'>
    <!-- Navegación -->
    <b-navbar toggleable='md' type='dark' variant='dark'>
      <b-container>
        <b-navbar-toggle target='nav-collapse'></b-navbar-toggle>
        <b-navbar-brand to='/'>AgroProgressive</b-navbar-brand>
        <b-collapse is-nav id='nav-collapse'>
          <b-navbar-nav>
            <!-- Selector de tambos -->
            <b-dropdown id='dropdown-tambo' :text='tamboElegido' right>
              <b-dropdown-item-button
                v-for='(tambo, index) of tambos'
                :key='tambo.id'
                @click='elegirTambo(index)'
              >
                <!-- hacer for en la lista de tambos de un archivo -->
                {{ tambo.nombre }}
              </b-dropdown-item-button>
              <b-dropdown-divider></b-dropdown-divider>
              <b-dropdown-item-button
                v-b-modal.modal-editarTambo
                @click='nuevoTambo()'
                >Añadir nuevo tambo</b-dropdown-item-button
              >
              <b-dropdown-item-button
                v-b-modal.modal-editarTambo
                @click='editarTambo()'
                >Editar tambos</b-dropdown-item-button
              >
            </b-dropdown>

            <!-- Menú de botones -->
            <b-nav-item to='/'>Inicio</b-nav-item>
            <b-nav-item to='/animales'>Animales</b-nav-item>
            <b-nav-item to='/crias'>Crías</b-nav-item>
            <b-nav-item to='/produccion'>Producción</b-nav-item>
            <b-nav-item to='/reproduccion'>Reproducción</b-nav-item>
            <b-nav-item to='/tacto'>Tacto</b-nav-item>
            <b-nav-item to='/historial'>Historial</b-nav-item>
            <b-nav-item to='/inconsistencias'>Inconsistencias</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>

    <!-- Contenido -->
    <router-view class='text-center' />
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex';

export default {
  name: 'app',
  computed: {
    ...mapState(['tambos', 'tamboElegido', 'tipoEdicionElegido']),
  },
  methods: {
    ...mapMutations(['elegirTambo', 'nuevoTambo', 'editarTambo']),
  },
};
</script>
