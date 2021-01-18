<template>
    <card class="flex flex-col items-center justify-center">
        <div class="px-12 py-12">
            <h1 class="text-center text-3xl text-80 font-light">Exchange Rates(INR)</h1>
            <table>
                <thead>
                    <tr>
                        <th>USD</th>
                        <th>GBP</th>
                        <th>EUR</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>{{ rate.USD }}</td>
                        <td>{{ rate.GBP }}</td>
                        <td>{{ rate.EUR }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
        
    </card>
</template>

<script>
export default {
    props: [
        'card',

        // The following props are only available on resource detail cards...
        // 'resource',
        // 'resourceId',
        // 'resourceName',
    ],
    data : function() {
        return {
            rate: []
        }
    },
    computed: async function() {
        let r= this;
        const response = await fetch('https://api.exchangeratesapi.io/latest?base=INR');
        let data =  await response.json();    
        r.rate.USD = data.rates.USD;
        r.rate.GBP = data.rates.GBP;
        r.rate.EUR = data.rates.EUR;
          
    
        
    }
}
</script>
