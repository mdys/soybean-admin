<script lang="ts" setup>
import { computed } from 'vue';
import { $t } from '@/locales';

defineOptions({ name: 'ExceptionBase' });

const props = defineProps<Props>();

type ExceptionType = '403' | '404' | '500';

interface Props {
  /**
   * Exception type
   *
   * - 403: no permission
   * - 404: not found
   * - 500: service error
   */
  type: ExceptionType;
}

const iconMap: Record<ExceptionType, string> = {
  '403': 'no-permission',
  '404': 'not-found',
  '500': 'service-error'
};

const icon = computed(() => iconMap[props.type]);
</script>

<template>
  <div class="flex-vertical-center gap-24px min-h-520px wh-full overflow-hidden">
    <div class="flex text-400px text-primary">
      <SvgIcon :local-icon="icon" />
    </div>
    <RouterLink to="/">
      <NButton type="primary">{{ $t('common.backToHome') }}</NButton>
    </RouterLink>
  </div>
</template>

<style scoped></style>
