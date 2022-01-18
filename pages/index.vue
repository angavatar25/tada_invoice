<template>
  <div class=" bg-gray-100 min-h-screen">
    <div class="max-w-6xl m-auto py-4">
      <h1 class="text-2xl font-bold mb-6">Invoice Dashboard</h1>
      <div>
        <InvoiceList :tableData="dummy" @OpenInvoiceDetail="showInvoiceDetail"/>
      </div>
      <div class="mt-10">
        <InvoiceDetail 
          :invoiceDetailOpen="openInvoiceDetail" 
          :detail="invoiceDetail"
          @CloseInvoiceDetail="openInvoiceDetail = false"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  head() {
    return {
      title: 'Invoice Dashboard'
    }
  },
  data() {
      return {
          dummy: [
              {
                id: 1, 
                invoice: 'ZGA-8789-AG', 
                due_date: '12-10-2023 18:30', 
                amount: '19150',
                shipping_cost: '150',
                status: 1,
                shipping_detail: {
                  date_issued: '14/10/2020',
                  date_arrival: '17/10/2020',
                  invoice: 'ZGA-8789-AG',
                  shipping_city: 'Barcelona',
                  shipping_country: 'Spain',
                  shipping_address: 'El Dorado del Vincente, 243HQ, City of Barcelona',
                  shipping_num: '+347890192',
                  destination_detail: {
                    destination_city: 'London',
                    destination_country: 'United Kindgom',
                    destination_address: 'Merchant Street, 196L, Croydon',
                    destination_num: '+4475569129',
                  },
                  items_detail: {
                    item: 'NVIDAI GeForce RTX2080 Ti',
                    amount: 10,
                    price_per_item: '1900'
                  }
                },
              },
              {
                id: 1, 
                invoice: 'ZGA-8789-AG', 
                due_date: '12-10-2023 18:30', 
                amount: '19132',
                shipping_cost: '132',
                status: 2,
                shipping_detail: {
                  date_issued: '14/10/2020',
                  date_arrival: '-',
                  invoice: 'ZGA-8789-AG',
                  shipping_city: 'Madrid',
                  shipping_country: 'Spain',
                  shipping_address: 'El Dorado del Vincente, 243HQ, City of Madrid',
                  shipping_num: '+347890192',
                  destination_detail: {
                    destination_city: 'London',
                    destination_country: 'United Kindgom',
                    destination_address: 'Merchant Street, 196L, Croydon',
                    destination_num: '+4475569129',
                  },
                  items_detail: {
                    item: 'NVIDAI GeForce RTX2080 Ti',
                    amount: 10,
                    price_per_item: '1900'
                  }
                },
              },
                            {
                id: 1, 
                invoice: 'ZGA-8789-AG', 
                due_date: '12-10-2023 18:30', 
                amount: '19089', 
                shipping_cost: '89',
                status: 3,
                shipping_detail: {
                  date_issued: '14/10/2020',
                  date_arrival: '-',
                  invoice: 'ZGA-8789-AG',
                  shipping_city: 'Paris',
                  shipping_country: 'France',
                  shipping_address: 'El Dorado del Vincente, 243HQ, City of Paris',
                  shipping_num: '+347890192',
                  destination_detail: {
                    destination_city: 'London',
                    destination_country: 'United Kindgom',
                    destination_address: 'Merchant Street, 196L, Croydon',
                    destination_num: '+4475569129',
                  },
                  items_detail: {
                    item: 'NVIDAI GeForce RTX2080 Ti',
                    amount: 10,
                    price_per_item: '1900'
                  }
                },
              },
                            {
                id: 1, 
                invoice: 'ZGA-8789-AG', 
                due_date: '12-10-2023 18:30', 
                amount: '19350',
                shipping_cost: '350',
                status: 1,
                shipping_detail: {
                  date_issued: '14/10/2020',
                  date_arrival: '17/10/2020',
                  invoice: 'ZGA-8789-AG',
                  shipping_city: 'Kyiv',
                  shipping_country: 'Ukraine',
                  shipping_address: 'El Dorado del Vincente, 243HQ, City of Kyiv',
                  shipping_num: '+347890192',
                  destination_detail: {
                    destination_city: 'London',
                    destination_country: 'United Kindgom',
                    destination_address: 'Merchant Street, 196L, Croydon',
                    destination_num: '+4475569129',
                  },
                  items_detail: {
                    item: 'NVIDAI GeForce RTX2080 Ti',
                    amount: 10,
                    price_per_item: '1900'
                  }
                },
              },
          ],
          openInvoiceDetail: false,
          invoiceDetail: {}
      }
  },
  methods: {
    showInvoiceDetail(data) {
      this.openInvoiceDetail = true,
      this.invoiceDetail = data
    }
  }
}
</script>

<style>

</style>
