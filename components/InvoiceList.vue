<template>
    <div class="bg-white p-5 rounded-md">
        <div class="flex gap-10 mb-6 border-b border-gray-300">
            <button :class="currentStatus === 'all' ? 'border-black border-b' : ''" class="pb-5" @click="filterStatus('all')">All</button>
            <button :class="currentStatus === 'paid' ? 'border-black border-b ' : ''" class="pb-5" @click="filterStatus('paid')">Paid</button>
            <button :class="currentStatus === 'pending' ? 'border-black border-b' : ''" class="pb-5" @click="filterStatus('pending')">Pending</button>
            <button :class="currentStatus === 'cancelled' ? 'border-black border-b' : ''" class="pb-5" @click="filterStatus('cancelled')">Cancelled</button>
        </div>
        <table class="table">
            <tr class="text-left">
                <th></th>
                <th>Invoice Number</th>
                <th>Due Date</th>
                <th>Amount</th>
                <th>Status</th>
                <th>Action</th>
            </tr>
            <template v-for="data in tableResult">
                <tr class="border-b border-gray-200 hover:bg-orange-200" :key="data.i">
                    <td>
                        <div class="w-8 h-8 flex justify-center items-center rounded-full bg-orange-300 text-white">
                            <i class="far fa-file-alt"></i>
                        </div>
                    </td>
                    <td>{{ data.invoice }}</td>
                    <td>{{ data.due_date }}</td>
                    <td>${{ formatNumber(data.amount) }}</td>
                    <td>
                        <div class="flex">
                            <div :class="statusBullet(data.status)" class="w-2 h-2 my-auto rounded-full"></div>
                            <span class="ml-4">{{ statusLabel(data.status) }}</span>
                        </div>
                    </td>
                    <td>
                        <button @click="viewDetail(data)" class="bg-blue-500 text-white px-4 py-2 rounded-md">
                            <i class="fas fa-receipt"></i>
                            View Detail
                        </button>
                    </td>
                </tr>
            </template>
        </table>
    </div>
</template>

<script>
export default {
    props: {
        tableData: {
            type: Array
        }
    },
    data() {
        return {
            tableResult: this.tableData,
            currentStatus: 'all'
        }
    },
    methods: {
        viewDetail(data) {
            this.$emit('OpenInvoiceDetail', data)
        },
        statusLabel(status) {
            let label = ''
            if(status === 1) {
                label = 'Paid'
            } else if(status === 2) {
                label = 'Pending'
            } else if(status === 3) {
                label = 'Cancelled'
            }
            return label
        },
        formatNumber(number)  {
          return number.toString().replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")
        },
        statusBullet(status) {
            let label = ''
            if(status === 1) {
                label = 'bg-green-500'
            } else if(status === 2) {
                label = 'bg-orange-500'
            } else if(status === 3) {
                label = 'bg-red-500'
            }
            return label
        },
        filterStatus(status) {
            if(status === 'paid') {
                this.currentStatus = 'paid'
                this.tableResult = this.tableData.filter(e => {
                    return e.status === 1
                })
            } else if(status === 'pending') {
                this.currentStatus = 'pending'
                this.tableResult = this.tableData.filter(e => {
                    return e.status === 2
                })
            } else if(status === 'cancelled') {
                this.currentStatus = 'cancelled'
                this.tableResult = this.tableData.filter(e => {
                    return e.status === 3
                })
            } else {
                this.currentStatus = 'all'
                this.tableResult = this.tableData
            }
        }
    }
}
</script>

<style>
table {
    width: 100%;
}
td {
    @apply py-3
}
</style>