<template>
  <RouterLink
    :to="{ name: 'Invoice', params: { invoiceId: props.data?.docId } }"
    class="flex invoice"
  >
    <div class="left flex">
      <span class="docId">{{ props.data?.docId }}</span>
      <span class="due-date">{{ props.data?.paymentDueDate }}</span>
      <span class="client">{{ props.data?.clientName }}</span>
    </div>
    <div class="right flex">
      <span class="price">{{ props.data?.invoiceTotal }}</span>
      <div
        class="status-button"
        :class="{
          pending: data?.invoicePending,
          draft: data?.invoiceDraft,
          paid: data?.invoicePaid
        }"
      >
        <span v-if="data?.invoicePending">Pending</span>
        <span v-if="data?.invoiceDraft">Draft</span>
        <span v-if="data?.invoicePaid">Paid</span>
      </div>
      <div class="icon">
        <img src="@/assets/r-arrow.png" alt="" height="12px" width="12px" />
      </div>
    </div>
  </RouterLink>
</template>

<script setup lang="ts">
import { defineProps } from 'vue'
import type { PropType } from 'vue'
import type { invoice } from '@/interface/IInvoice'

import { RouterLink } from 'vue-router'
const props = defineProps({
  data: {
    type: Object as PropType<invoice>,
    requierd: true
  }
})
</script>
