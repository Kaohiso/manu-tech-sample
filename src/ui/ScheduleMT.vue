<script setup lang="ts">
interface Rows {
  key: string
  firstValue?: string
  lastValue: string
}

interface PropsSchedule {
  content: Rows[]
}

defineProps<PropsSchedule>()

function updateColorWhenClosed(status: string) {
  if (status === 'Fermé') {
    return 'color: var(--sys-color-status-closed)'
  }
}
</script>

<template>
  <div class="container">
    <div v-for="row in content" class="schedule">
      <p class="key">{{ row.key }}</p>
      <p>
        <span class="value first-value">{{ row.firstValue }}</span>

        <span class="value last-value" :style="updateColorWhenClosed(row.lastValue)">
          {{ row.lastValue }}
        </span>
      </p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  gap: 20px;

  .schedule {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(50px, 1fr));

    > p:last-child {
      display: flex;
      justify-content: end;
      flex-wrap: wrap;

      > span:nth-of-type(2) {
        margin-left: 20px;
      }
    }

    .key {
      color: var(--sys-color-text-tertiary);
    }

    .value {
      color: var(--sys-color-text-primary);
      font-family: var(--ref-font-family-mono);
    }

    .first-value {
      text-align: start;
      grid-column-start: 4;
    }

    .last-value {
      text-align: end;
      grid-column-start: 5;
    }
  }
}

@media (max-width: 768px) {
  .container {
    .schedule {
      > p {
        font-size: 12px;
      }
    }
  }
}
</style>
