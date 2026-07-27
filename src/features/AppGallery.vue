<script lang="ts" setup>
import AppSection from '@/features/layout/AppSection.vue'
import EyebrowMT from '@/ui/EyebrowMT.vue'
import zoe from '@/assets/images/gallery/zoe.jpeg'
import rLink from '@/assets/images/gallery/r-link.jpeg'
import volkswagen from '@/assets/images/gallery/volkswagen.jpeg'
import pcb from '@/assets/images/gallery/pcb.jpeg'
import chip from '@/assets/images/gallery/chip.jpeg'
import monitor from '@/assets/images/gallery/monitor.jpeg'
import led from '@/assets/images/gallery/led.jpeg'
import ps2 from '@/assets/images/gallery/ps2.jpeg'
import nintendo from '@/assets/images/gallery/nintendo.jpeg'
import samsung from '@/assets/images/gallery/samsung.jpeg'

interface Props {
  id: number
  src: string
  alt: string
}

const images: Props[] = [
  {
    id: 1,
    src: zoe,
    alt: "Écran tactile d'une Renault Zoé avec navigation et musique",
  },
  {
    id: 2,
    src: rLink,
    alt: "Écran multimédia R-Link d'un véhicule Renault",
  },
  {
    id: 3,
    src: volkswagen,
    alt: 'Autoradios Volkswagen en cours de mise à jour logicielle',
  },
  {
    id: 4,
    src: pcb,
    alt: 'Carte électronique de calculateur automobile (ECU) ouverte',
  },
  {
    id: 5,
    src: chip,
    alt: 'Gros plan sur une puce électronique soudée sur circuit imprimé',
  },
  {
    id: 6,
    src: monitor,
    alt: 'Écran affichant le logo Manu-Tech, diagnostic auto et réparation électronique',
  },
  {
    id: 7,
    src: led,
    alt: "Dalle de rétroéclairage LED d'un téléviseur démontée",
  },
  {
    id: 8,
    src: ps2,
    alt: 'Console PlayStation 2 allumée devant un téléviseur',
  },
  {
    id: 9,
    src: nintendo,
    alt: "Carte mère d'une console Nintendo Switch ouverte",
  },
  {
    id: 10,
    src: samsung,
    alt: 'Smartphone Samsung allumé posé sur son emballage',
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
