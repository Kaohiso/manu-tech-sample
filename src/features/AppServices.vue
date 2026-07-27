<script lang="ts" setup>
import EyebrowMT from '@/ui/EyebrowMT.vue'
import * as Icons from '@lucide/vue'
import ServiceMT from '@/ui/ServiceMT.vue'
import AppVehicles from '@/features/AppVehicles.vue'
import AppSection from '@/features/layout/AppSection.vue'
import carDiagnostic from '@/assets/images/ai-diagnostic.jpeg'
import repairSmartphone from '@/assets/images/ai-repair.jpeg'

interface dataItemListProps {
  iconName: Icons.LucideIcon
  text: string
}

const itemListDiagnosis: dataItemListProps[] = [
  { iconName: Icons.SearchIcon, text: 'Diagnostic électronique ECU & Modules annexes' },
  { iconName: Icons.CircleAlertIcon, text: 'Calibration boîte de vitesses' },
  { iconName: Icons.ActivityIcon, text: 'Test complet de la santé de la batterie' },
  { iconName: Icons.RefreshCcwIcon, text: 'Activation CarPlay / Android Auto' },
  { iconName: Icons.SettingsIcon, text: 'Mise à jour Firmware / GPS' },
  { iconName: Icons.RadioIcon, text: 'Initialisation capteurs TPMS' },
  { iconName: Icons.ToggleRightIcon, text: "Activation d'options" },
  { iconName: Icons.KeyIcon, text: 'Programmation de clé ou carte avec code PIN' },
]

const itemListRepair: dataItemListProps[] = [
  { iconName: Icons.SmartphoneIcon, text: 'Remplacement écran smartphone' },
  { iconName: Icons.GamepadIcon, text: 'Réparation console de jeux' },
  { iconName: Icons.TabletIcon, text: 'Remplacement écran tablette' },
  { iconName: Icons.BatteryIcon, text: 'Remplacement de batterie' },
  { iconName: Icons.MonitorIcon, text: 'Remplacement écran PC' },
  { iconName: Icons.ShieldIcon, text: 'Pose de film Hydrogel' },
  { iconName: Icons.LightbulbIcon, text: 'Remplacement rétroéclairage LED' },
  { iconName: Icons.DrillIcon, text: 'Remplacement pièce électroménager' },
]
</script>

<template>
  <AppSection class="app-services" id-section="services">
    <header>
      <EyebrowMT>Nos prestations</EyebrowMT>
      <h2>
        <span>Expertise complète</span>
        <span> résultats garantis</span>
      </h2>
      <p>
        De l’automobile aux appareils grand public — nous intervenons sur tous vos équipements
        électroniques avec précision et professionnalisme.
      </p>
    </header>

    <ServiceMT
      :graphicIcon="Icons.CarIcon"
      :listServices="itemListDiagnosis"
      :imgSrc="carDiagnostic"
      altSrc="Illustration d'un diagnostic automobile"
    >
      <template #heading>Diagnostic Electronique Automobile</template>
      <template #subheading>Diagnostic · Codage · Apprentissage</template>
      <template #description>
        Equipé des derniers outils de diagnostic professionnel, nous intervenons sur l'ensemble des
        systèmes électroniques de votre véhicule : lecture des codes défauts, codage, activation
        d'options et bien plus encore.
      </template>
      <template #image-heading>Diagnostic complet</template>
      <template #image-subheading>Toutes marques & modèles</template>
      <template #image-price>35€</template>
      <template #image-subprice>tarif fixe</template>
    </ServiceMT>

    <AppVehicles />

    <ServiceMT
      direction="img-left"
      :graphicIcon="Icons.HammerIcon"
      :listServices="itemListRepair"
      :imgSrc="repairSmartphone"
      altSrc="Illustration d'une réparation d'écran de smartphone"
    >
      <template #heading>Réparation Electronique</template>
      <template #subheading>Smartphones · Tablettes · Consoles</template>
      <template #description>
        Nous intervenons sur tous les appareils électroniques grand public avec rigueur et
        précision. Pièces d'origine ou haute qualité, garantie sur chaque intervention.
      </template>
      <template #image-heading>Remplacement écran</template>
      <template #image-subheading>Smartphone · Tablette · Console</template>
      <template #image-price>50€</template>
      <template #image-subprice>à partir de</template>
    </ServiceMT>
  </AppSection>
</template>

<style lang="css" scoped>
:deep(.app-services) {
  display: grid;
  align-items: center;
  gap: 64px;

  > header {
    display: grid;
    gap: 20px;
    text-align: center;

    h2 {
      > span {
        display: inline;
      }
    }

    & > p {
      max-width: 60ch;
      margin-inline: auto;
    }
  }
}
</style>
