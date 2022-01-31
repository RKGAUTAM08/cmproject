<template>
  <div id="app">
    <div class="main-page">
      <h1>Tag Wise Price Drop 2</h1>

      <button
        type="button"
        class="btn"
        @click="showModal();hideButton();"
        v-show="isButtonVisible"
      >
        Add Data
      </button>
      <div class="modal-backdrop" v-show="isModalVisible" @close="closeModal">
        <div class="modal">
          <header class="modal-header">
            <slot name="header">
              Tag Wise Price Drop Form
            </slot>
            <button
              type="button"
              class="btn-close"
              @click="closeModal(); showButton();"
            >
              x
            </button>
          </header>

          <section class="modal-body">
            <slot name="body">
              <form>
                  <div class="input-cont">
                    <label for="id">Id</label>
                    <input type="number" id="id" class="input-ele" v-model="datas.id">
                  </div>
                  <div class="input-cont">
                    <label for="tag">Tag</label>
                    <input type="text" id="tag" class="input-ele" v-model="datas.tag">
                  </div>
                  <div class="input-cont">
                    <label for="catalogue-name">Catalogue Name</label>
                    <input type="text" id="catalogue-name" class="input-ele" v-model="datas.catalogueName">
                  </div>
                  <div class="input-cont">
                    <label for="sku_id">SKU ID</label>
                    <input type="text" id="sku_id" class="input-ele" v-model="datas.skuId">
                  </div>
                  <div class="input-cont">
                    <label for="deal_price">Deal Price</label>
                    <input type="text" id="deal_price" class="input-ele" v-model="datas.dealPrice">
                  </div>
                  <div class="input-cont">
                    <label for="moq">MOQ</label>
                    <input type="text" id="moq" class="input-ele" v-model="datas.moq">
                  </div>
                  <div class="input-cont">
                    <label for="commission_percent">Commission Percent</label>
                    <input type="text" id="commission_percent" class="input-ele" v-model="datas.commissionPercent">
                  </div>
                  <div class="input-cont">
                    <label for="campaign_name">Campaign Name</label>
                    <input type="text" id="campaign_name" class="input-ele" v-model="datas.campaignName">
                  </div>
                  <div class="input-cont">
                    <label for="campaign_type">Campaign Type</label>
                    <input type="text" id="campaign_type" class="input-ele" v-model="datas.campaignType">
                  </div>
                  <div class="input-cont">
                    <label for="campaign_description">Campaign Description</label>
                    <input type="text" id="campaign_description" class="input-ele" v-model="datas.campaignDescription">
                  </div>
                  <div class="input-cont">
                    <label for="coupon_code">Coupon Code</label>
                    <input type="text" id="coupon_code" class="input-ele" v-model="datas.couponCode">
                  </div>
                  <div class="input-cont">
                    <label for="is_active">Is Active</label>
                    <input type="text" id="is_active" class="input-ele" v-model="datas.isActive">
                  </div>
                  <div class="input-cont">
                    <label for="start_time">Start Time</label>
                    <input type="text" id="start_time" class="input-ele" v-model="datas.startTime">
                  </div>
                  <div class="input-cont">
                    <label for="end_time">End Time</label>
                    <input type="text" id="end_time" class="input-ele" v-model="datas.endTime">
                  </div>
                  <div class="input-cont">
                    <label for="priority">Priority</label>
                    <input type="text" id="priority" class="input-ele" v-model="datas.priority">
                  </div>
                  <div class="input-cont">
                    <label for="created_at">Created at</label>
                    <input type="text" id="created_at" class="input-ele" v-model="datas.createdAt">
                  </div>
                  <div class="input-cont">
                    <label for="min_cart_value">Minimum Cart Value</label>
                    <input type="text" id="min_cart_value" class="input-ele" v-model="datas.minCartValue">
                  </div>
                  <div class="input-cont">
                    <label for="clubbing_key">Clubbing Key</label>
                    <input type="text" id="clubbing_key" class="input-ele" v-model="datas.clubbingKey">
                  </div>
                  <div class="input-cont">
                    <label for="use_case_filter">Use Case Filter</label>
                    <input type="text" id="use_case_filter" class="input-ele" v-model="datas.useCaseFilter">
                  </div>
                  <div class="input-cont">
                    <label for="disallowed">Disallowed</label>
                    <input type="text" id="disallowed" class="input-ele" v-model="datas.disallowed">
                  </div>
                  <div class="modal-buttons">
                      <div>
                          <button @click="save()" class="btn btn-green">Save</button>
                          <button @click="onSubmit(datas)" class="btn btn-green">Submit</button>
                      </div>
                      <div>
                          <button
                            type="button"
                            class="btn-green"
                            @click="closeModal(); showButton();"
                            >
                            Close Modal
                          </button>
                      </div>
                  </div>
              </form>
            </slot>
          </section>
        </div>
      </div>
      <div>
        <table class="table tbl-view">
          <hr>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Tag</th>
              <th scope="col">catalogue Name</th>
              <th scope="col">SKU ID</th>
              <th scope="col">Deal Price</th>
              <th scope="col">MOQ</th>
              <th scope="col">Commission Percent</th>
              <th scope="col">Campaign name</th>
              <th scope="col">Campaign Type</th>
              <th scope="col">Campaign Description</th>
              <th scope="col">coupan Code</th>
              <th scope="col">Is Active</th>
              <th scope="col">start Time</th>
              <th scope="col">End Time</th>
              <th scope="col">Priority</th>
              <th scope="col">Created At</th>
              <th scope="col">Min Cart Value</th>
              <th scope="col">Clubbing Key</th>
              <th scope="col">Use Case Filter</th>
              <th scope="col">Disallowed</th>
              <th scope="col">Edit</th>
              <th scope="col">Delete</th>
            </tr>
            <hr>
            <tr v-for='item in items' :key='item.id'>
              <td>{{ item.id }}</td>
              <td>{{ item.tag }}</td>
              <td>{{ item.catalogueName }}</td>
              <td>{{ item.skuId }}</td>
              <td>{{ item.dealPrice }}</td>
              <td>{{ item.moq }}</td>
              <td>{{ item.commissionPercent }}</td>
              <td>{{ item.campaignName }}</td>
              <td>{{ item.campaignType }}</td>
              <td>{{ item.campaignDescription }}</td>
              <td>{{ item.coupanCode }}</td>
              <td>{{ item.isActive }}</td>
              <td>{{ item.startTime }}</td>
              <td>{{ item.endTime }}</td>
              <td>{{ item.priority }}</td>
              <td>{{ item.createdAt }}</td>
              <td>{{ item.minCartValue }}</td>
              <td>{{ item.clubbingKey }}</td>
              <td>{{ item.useCaseFilter }}</td>
              <td>{{ item.disallowed }}</td>
              <th><button @click="editData(item.id)">Edit</button></th>
              <th><button @click="deleteData(item.id)">Delete</button></th>
            </tr>
        </table>
      </div>

      <!--<Modal
        v-show="isModalVisible"
        @close="closeModal"
      ></Modal>-->
    </div>
  </div>
</template>

<script>
  import axios from "axios";

  export default {
    name: 'App',
    data() {
      return{
        isModalVisible:false,
        isButtonVisible:true,
        items:{},
        editid:null,
        datas:{
          id:"",
          tag:"",
          catalogueName:"",
          skuId:"",
          dealPrice:"",
          moq:"",
          commissionPercent:"",
          campaignName:"",
          campaignType:"",
          campaignDescription:"",
          couponCode:"",
          isActive:"",
          startTime:"",
          endTime:"",
          priority:"",
          createdAt:"",
          minCartValue:"",
          clubbingKey:"",
          useCaseFilter:"",
          disallowed:"",
        }
      }
    },
    async mounted(){
      this.mainpage()
    },
    methods: {
      close() {
        this.$emit('close');
      },
      showButton(){
        this.isButtonVisible=true;
      },
      hideButton(){
        this.isButtonVisible = false;
      },
      showModal() {
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      },
      mainpage(){
        axios.get('http://localhost:3000/').then((res)=>{
          this.items=res.data;
        })
      },
      editData(id){
        this.editid=id;
        axios.get('http://localhost:3000/'+id).then((res)=>{
          this.datas=res.data[0];
        })
      },
      deleteData(id){
        axios.delete('http://localhost:3000/delete/'+id).then((res)=>{
          console.log(res.data)
          this.mainpage();
        })
      },
      onSubmit(datas){
        axios.post('http://localhost:3000/insert',datas).then((res)=>{
          console.log(res.data)
          this.mainpage();
        })
      },
      save(){
        axios.put('http://localhost:3000/insert/'+this.editid,this.datas).then((res)=>{
          console.log(res);
          this.mainpage();
        })
      },
    }
  };
</script>

<style>
  .main-page{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  hr{
        border: 1px solid gray;
        margin-left: auto;
        margin-right: auto;
        width: 100vw;
    }
    .tbl-view{
        display: flex;
        flex-direction: column;
    }
  .modal-header{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .btn-close {
    position: absolute;
    top: 0;
    right: 0;
    border: none;
    font-size: 20px;
    padding: 10px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
  }

  .btn-green {
    color: white;
    background: #4AAE9B;
    border: 1px solid #4AAE9B;
    width: 100px;
    height: 30px;
    border-radius: 2px;
  }
  
  .input-cont{
      display: flex;
      justify-content: space-between;
      margin: 20px;
  }

  .input-ele{
      width: 50%;
  }
  
  .radio-input{
      display: flex;
      justify-content: space-around;
  }

  .modal-buttons{
      display: flex;
      justify-content: space-around;
  }
  button:hover{
      border:1px solid black;
  }
</style>
