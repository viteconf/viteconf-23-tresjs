<script setup lang="ts">
import { extend } from '@tresjs/core';

import { reactive } from 'vue';
import { BasicShadowMap, SRGBColorSpace, NoToneMapping } from 'three';
import { TresCanvas } from '@tresjs/core';
import { RoundedBoxGeometry } from 'three-stdlib';
import { OrbitControls, Levioso } from '@tresjs/cientos';

const gl = {
  clearColor: '#82DBC5',
  shadows: true,
  alpha: false,
  shadowMapType: BasicShadowMap,
  outputColorSpace: SRGBColorSpace,
  toneMapping: NoToneMapping,
};

extend({ RoundedBoxGeometry });
</script>

<template>
  <TresCanvas v-bind="gl">
    <TresPerspectiveCamera :position="[9, 9, 9]" />
    <OrbitControls />
    <TresMesh cast-shadow>
      <TresRoundedBoxGeometry :args="[1, 1, 1, 7, 0.2]" />
      <TresMeshToonMaterial color="#82DBC5" />
    </TresMesh>
    <TresAxesHelper :args="[1]" />
    <TresDirectionalLight :position="[0, 2, 4]" :intensity="1.2" cast-shadow />
  </TresCanvas>
</template>
