<template>
  <div>
    <b-card border-variant='dark' header='Información del animal' class='mt-3 mb-3'>
      <infoBasica />
      <textoValor texto='Fecha de ingreso' valor='[valor]' />
    </b-card>
  </div>
</template>

<script>
import textoValor from '@/components/TextoValor.vue';
import infoBasica from '@/components/InfoBasica.vue';

export default {
  name: 'cardInfo',
  components: {
    textoValor,
    infoBasica,
  },
};
</script>