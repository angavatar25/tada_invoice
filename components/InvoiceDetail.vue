<template>
    <div v-if="invoiceDetailOpen">
        <div class="content bg-white p-5 rounded-md">
            <div class="flex justify-between mb-5">
                <p class="text-4xl  text-orange-500">Invoice</p>
                <button @click="closeDetail">
                   <i class="fas fa-times my-auto text-xl"></i>
                </button>
            </div>
            <div class="flex gap-6">
                <div class="flex">
                    <span>Date Shipped:</span>
                    <span>{{ detail.shipping_detail.date_issued }}</span>
                </div>
                <div class="flex">
                    <span>Date Arrival:</span>
                    <span>{{ detail.shipping_detail.date_arrival }}</span>
                </div>
                <div class="flex">
                    <span>Invoice No:</span>
                    <span>{{ detail.shipping_detail.invoice }}</span>
                </div>
            </div>
            <div class="flex gap-6">
            <div class="mt-5">
                <p>Total Amount</p>
                <p class=" text-orange-500 text-xl">$ {{ formatNumber(detail.amount) }}</p>
            </div>
            <div class="mt-5">
                <p>Shipping Cost</p>
                <p class=" text-orange-500 text-xl">$ {{ formatNumber(detail.shipping_cost) }}</p>
            </div>
            </div>
            <div class="mt-5">
                <p class="mb-4 text-xl border-b border-dashed border-gray-300 pb-3">Transaction Detail</p>
                <div class="flex gap-6">
                    <div>
                        <p class="mb-2">Shipping from</p>
                        <p class=" text-2xl">{{detail.shipping_detail.shipping_city}}, {{detail.shipping_detail.shipping_country}}</p>
                        <p>{{ detail.shipping_detail.shipper }}</p>
                        <p>{{ detail.shipping_detail.shipping_address }}</p>
                        <p>{{ detail.shipping_detail.shipping_num }}</p>
                    </div>
                    <i class="fas fa-arrow-right my-auto text-2xl text-orange-500"></i>
                    <div>
                        <p class="mb-2">Destination</p>
                        <p class="text-2xl">{{ detail.shipping_detail.destination_detail.destination_city }}, {{detail.shipping_detail.destination_detail.destination_country}}</p>
                        <p>{{ detail.shipping_detail.destination_detail.receiver }}</p>
                        <p>{{ detail.shipping_detail.destination_detail.destination_address }}</p>
                        <p>{{ detail.shipping_detail.destination_detail.destination_num }}</p>
                    </div>
                </div>
                <div class="mt-5 flex gap-6">
                    <div>
                        <p>Items</p>
                        <p>{{ detail.shipping_detail.items_detail.item }}</p>
                    </div>
                    <div>
                        <p>Amount</p>
                        <p>{{ detail.shipping_detail.items_detail.amount }}x</p>
                    </div>
                    <div>
                        <p>Price per Item</p>
                        <span>$ {{ formatNumber(detail.shipping_detail.items_detail.price_per_item) }} per item</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        invoiceDetailOpen: {
            type: Boolean
        },
        detail: {
            type: Object
        }
    },
    methods: {
        formatNumber(number)  {
          return number.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")
        },
        closeDetail() {
            this.$emit("CloseInvoiceDetail")
        }
    }
}
</script>

<style>

</style>