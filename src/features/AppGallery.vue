<script lang="ts" setup>
import AppSection from '@/features/layout/AppSection.vue'
import EyebrowMT from '@/ui/EyebrowMT.vue'
import centerConsoleZoe from '@/assets/images/gallery/center-console-zoe.jpg'
import ecu from '@/assets/images/gallery/ecu.jpg'
import electronicComponent from '@/assets/images/gallery/electronic-component.jpg'
import krups from '@/assets/images/gallery/krups.jpg'
import nintendoSwitch from '@/assets/images/gallery/nintendo-switch.jpg'
import pcbCar from '@/assets/images/gallery/pcb-car.jpg'
import pcbLaptop from '@/assets/images/gallery/pcb-laptop.jpg'
import puceSoic from '@/assets/images/gallery/puce-soic.jpg'
import rLink from '@/assets/images/gallery/r-link.jpg'
import tvLed from '@/assets/images/gallery/tv-led.jpg'

interface Props {
  id: number
  src: string
  alt: string
}

const images: Props[] = [
  {
    id: 1,
    src: centerConsoleZoe,
    alt: "Console centrale d'une Renault Zoé, avec écran affichant Android Auto (carte GPS et lecteur de musique), commandes de climatisation.",
  },
  {
    id: 2,
    src: ecu,
    alt: "Carte électronique complète d'un calculateur moteur (ECU) automobile, ouverte, avec de nombreux composants soudés dont un microcontrôleur Infineon visible, posée sur un établi.",
  },
  {
    id: 3,
    src: electronicComponent,
    alt: 'Composant électronique démonté pour diagnostic',
  },
  {
    id: 4,
    src: krups,
    alt: "Détail du panneau de contrôle d'une machine à café Krups, montrant les voyants (détartrage, température).",
  },
  {
    id: 5,
    src: nintendoSwitch,
    alt: "Intérieur d'une console Nintendo Switch démontée, montrant la carte mère, le ventilateur et la batterie (référence HAC-003 visible).",
  },
  { id: 6, src: pcbCar, alt: 'img1' },
  {
    id: 7,
    src: pcbLaptop,
    alt: "Intérieur d'un ordinateur portable ouvert, montrant la carte mère, le ventilateur, un SSD, la RAM et la batterie.",
  },
  {
    id: 8,
    src: puceSoic,
    alt: "Photo macro (très rapprochée) d'un composant électronique (puce SOIC à 8 broches) soudé sur un circuit imprimé, référence '28000766' visible.",
  },
  {
    id: 9,
    src: rLink,
    alt: "Écran tactile d'un système multimédia embarqué Renault (R-LINK), affichant l'interface Apple CarPlay avec les icônes Téléphone, Musique, Plans, Messages.",
  },
  {
    id: 10,
    src: tvLed,
    alt: "Panneau arrière d'un écran de télévision LED démonté, avec les bandes de rétroéclairage (LED strips) allumées et visibles.",
  },
]
</script>

<template>
  <AppSection class="app-gallery" id-section="gallery">
    <EyebrowMT>Galerie atelier</EyebrowMT>
    <div class="container-gallery">
      <img
        v-for="image in images"
        :key="image.id"
        :src="image.src"
        :alt="image.alt"
        class="image-gallery"
      />
    </div>
  </AppSection>
</template>

<style scoped>
:deep(.app-gallery) {
  display: grid;
  gap: 20px;

  .container-gallery {
    display: flex;
    overflow-x: scroll;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    gap: 20px;
    anchor-name: --gallery;

    &::-webkit-scrollbar {
      display: none;
    }

    & {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }

    &::scroll-button(inline-start) {
      content: '←';
      position: fixed;
      position-anchor: --gallery;
      top: anchor(center);
      left: anchor(left);
      font-size: var(--ref-size-20);
      translate: -50% -50%;
      aspect-ratio: 1/1;
      border: 2px solid hsl(from var(--sys-color-primary) h s l / 0.15);
      background-color: var(--app-background-on-background);
      border-radius: var(--app-radius-icon);
      color: var(--sys-color-text-primary);
    }

    &::scroll-button(inline-end) {
      content: '→';
      position: fixed;
      position-anchor: --gallery;
      top: anchor(center);
      left: anchor(right);
      font-size: var(--ref-size-20);
      translate: -50% -50%;
      aspect-ratio: 1/1;
      border: 2px solid hsl(from var(--sys-color-primary) h s l / 0.15);
      background-color: var(--app-background-on-background);
      border-radius: var(--app-radius-icon);
      color: var(--sys-color-text-primary);
    }

    .image-gallery {
      scroll-snap-align: center;
      flex-shrink: 0;
      object-fit: cover;
      width: min(350px, 100%);
      height: 200px;
    }
  }
}

@media (max-width: 1024px) {
  .container-gallery {
    &::scroll-button(inline-start) {
      display: none;
    }

    &::scroll-button(inline-end) {
      display: none;
    }
  }
}
</style>
