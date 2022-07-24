<template>

    <div v-if="records.length" class="w-full flex justify-center ">
        <div class="w-full md:w-3/6 flex flex-col  ">
            <div v-for="(record, i) in records" :key="i">
                <Card :type="record.type" :product="record.product" :message="record.message" :date="record.date" :time="record.time" />
            </div>
        </div>
    </div>

    <div v-if="!records.length" class="w-full flex justify-center">
        <Spinner />
    </div>

</template>

<script>
import axios from 'axios'
import Spinner from '../components/Spinner.vue'
import Card from '../components/RecordCard.vue'

export default {
    components:{
        Spinner,
        Card
    },
    data() {
        return {
            records: [],
        };
    },
    async created(){
        await axios.get('http://localhost:8000/api/records').then((result) => {
            this.records = result.data;
            !this.records.length ? this.records = [{message: 'no records saved'}] : '';
        });
    }
}
</script>
