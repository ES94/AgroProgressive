<template>
  <div class='home'>
    <b-container class='mt-3 mb-3'>
      <b-row align-h='center' align-v='center'>
        <b-col lg='6' md='6' sm='10'>
          <b-card border-variant='dark' header='Elija una opción para comenzar'>
            <b-list-group flush>
              <b-list-group-item>
                <b-button
                  pill
                  variant='primary'
                  v-b-modal.modal-editarTambo
                  @click='nuevoTambo()'
                >
                  Añadir nuevo tambo</b-button
                >
              </b-list-group-item>
              <b-list-group-item>
                <b-button
                  pill
                  variant='primary'
                  v-b-modal.modal-selecTambo
                  @click='editarTambo()'
                >
                  Elegir tambo</b-button
                >
              </b-list-group-item>
              <b-list-group-item>
                <b-button
                  pill
                  variant='primary'
                  @click='probarNotif()'
                >
                  Demo notificación</b-button
                >
              </b-list-group-item>
            </b-list-group>
          </b-card>
        </b-col>
      </b-row>
    </b-container>

    <!-- Cuadro modal de edición de tambo -->
    <edicionTambo :tipoEdicion='tipoEdicionElegido' />

    <!-- Cuadro modal de selección de tambo -->
    <selecTambo />
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex';
import edicionTambo from '@/components/EdicionTambo.vue';
import selecTambo from '@/components/SeleccionTambo.vue';

export default {
  name: 'inicio',
  components: {
    edicionTambo,
    selecTambo,
  },
  computed: {
    ...mapState(['tambos', 'tamboElegido', 'tipoEdicionElegido']),
  },
  methods: {
    ...mapMutations([
      'elegirTambo',
      'nuevoTambo',
      'editarTambo',
    ]),
    probarNotif() {
      /* Opciones de notificación */
      const opt = {
        type: 'success',
        icon: 'mdi-check',
        position: 'bottom-right',
        theme: 'bubble',
        closeOnSwipe: true,
        singleton: true,
      };

      /* Lanza una notificación que dura dos segundos */
      this.$toasted.show('prueba notificación', opt).goAway(2000);
    },
  },
};
</script>
