<template>
    <router-link :to="{name: 'Validation', params: {absenceId: absence.id}}" custom v-slot="{navigate, href}">
        <a class="list-group-item list-group-item-action d-flex justify-content-between align-items-center" @click="navigate" :href="href">

            <div class="fs-6">
                {{formatDateFr(absence.dd)}} <i class="bi bi-chevron-compact-right"></i> {{formatDateFr(absence.df)}}
            </div>
            <div class="fs-6">{{absence.id}}</div>
            <div class="fs-6">
                <span v-if="absence.valider === null" class="text-warning">En attente</span>
                <span v-else-if="absence.valider === 'OUI'" class="text-success">Validée</span>
                <span v-else class="text-danger">Refusée</span>
            </div>
        </a>
    </router-link>
</template>

<script>

import formatDateFr from '../js/formatDateFr';

export default {
    props: {
        absence: Object
    },

    methods: {

        formatDateFr(date) {
            return formatDateFr(date);
        }        

    }

}



</script>