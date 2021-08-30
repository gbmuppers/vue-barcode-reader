<template>
    <div class="table-responsive" style="margin-top:0rem;">
      <button class="btn btn-outline-primary btn-block" @click="reset()">Reset</button>
      <table class="table">
        <thead>
          <tr>
            <th>Intento</th>
            <th>Codigo</th>
            <th>Formato</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(scanner,index) in list_decoded_barcode" :key="index">
            <td>{{index}}</td>
            <td>{{scanner.codigo}}</td>
            <td>{{scanner.formato}}</td>
          </tr>
        </tbody>
      </table>
    <div class="container" style="margin-bottom:1rem;">
      <StreamBarcodeReader
            @decode="onDecode"
            @loaded="onLoaded"
        ></StreamBarcodeReader>
    </div>
  </div>
</template>

<script>

import { StreamBarcodeReader } from "vue-barcode-reader";
export default {
    components:{
        StreamBarcodeReader
    },
    data(){
        return{
            list_decoded_barcode:[],
        }
    },
    methods:{
        onDecode(result){
            this.list_decoded_barcode.push({codigo:result,formato:'SIN DEFINIR'})
        },
        reset(){
            this.list_decoded_barcode = []
        }
    }
}
</script>