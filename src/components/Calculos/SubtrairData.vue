<template>
    <q-card-section class="col-12 col-md-4">
        <div class="text-h5 q-mt-sm q-mb-md">Subtrair Datas</div>

        <q-input color="dark" outlined bottom-slots v-model="text" label="Data 1" stack-label type="date"/>

        <q-input color="dark" outlined bottom-slots v-model="text" label="Data 2" stack-label type="date"/>
        
        <q-btn-group push spread>
            <q-btn flat size="100" label="Calcular" class="bg-dark" color="white" />
            <q-btn flat label="6325" color="dark" />
        </q-btn-group>
        
    </q-card-section>
</template>