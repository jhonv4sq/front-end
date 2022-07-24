<template>

        <div class="relative flex flex-col justify-end overflow-hidden rounded-b-xl w-full pt-6">
            <div class="group relative flex cursor-pointer justify-between rounded-xl  before:absolute before:inset-y-0 before:right-0 before:w-1/2 before:rounded-r-xl before:bg-gradient-to-r before:from-transparent  before:opacity-0 before:transition before:duration-500 hover:before:opacity-100" :class="this.type ? 'bg-blue-200 before:to-blue-600' : 'bg-red-200 before:to-red-600'">
                <div class="relative space-y-1 p-4 w-full flex flex-col gap-5">
                    <p class="text-xl font-bold text-center" :class="this.type ? 'text-blue-900' : 'text-red-900'">{{ this.product }}</p>
                    <p class="text-xl text-center" :class="this.type ? 'text-blue-900' : 'text-red-900'">{{ this.message }}</p>
                    <div class="flex w-full justify-around">
                        <p class="text-xl" :class="this.type ? 'text-blue-900' : 'text-red-900'">{{ this.date }}</p>
                        <p class="text-xl" :class="this.type ? 'text-blue-900' : 'text-red-900'">{{ this.time }}</p>
                    </div>
                </div>
            </div>
        </div>

</template>

<script>
export default {
  props:{
    type: Number,
    product: String,
    message: String,
    date: String,
    time: String,
  },
}
</script>
