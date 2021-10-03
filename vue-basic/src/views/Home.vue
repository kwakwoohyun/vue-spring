<template>
    <div>
        <h1>Welcome {{ title }}</h1>
        <input type="text" v-model="input1"/>
        <button type="button" @click="getData">GET</button>
        <button type="button" @click="setData">SET</button>

        <select class="form-control" v-model="region" @change="changeRegion">
            <option :key="i" :value="d.v" v-for="(d,i) in options">
                {{ d.t }}
            </option>
        </select>

        <!-- v-if, v-show 차이점 v-if는 랜더링을 안함, v-show는 랜더링은 하는데 보여주지 않음 -->
        <!-- 특정화면에서 자주 보였다 안보였다 하는작업은 v-show를 해야함 v-if는 리소스가 들기때문 -->
        <table class="table table-bordered" v-if="tableShow">
            <tr :key="i" v-for="(d,i) in options">
                <td>{{ d.v }}</td>
                <td>{{ d.t }}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
    data(){
        return{
            title: "반갑습니다.",
            input1: "곽우현",
            options: [
                {
                    v:"S",
                    t:"Seoul"
                },
                {
                    v:"J",
                    t:"Jeju"
                },
                {
                    v:"B",
                    t:"Busan"
                },
            ],
            region: "J",
            tableShow: false,
        }
    },
    // 변경시 감지
    watch:{
        input1(){
            // input1 데이터가 변경됬을때
            console.log(this.input1);
        },
        title(){

        }
    },
    methods:{
        getData(){
            alert(this.input1);
        },
        setData(){
            this.input1="홍바오";
        },
        changeRegion(){
            alert(this.region);
        }
    },
    // life cycle
    beforeCreate(){
            console.log("beforeCreate");
    },
    created(){
            console.log("created");
    },
    beforeMount(){
            console.log("beforeMount");
    },
    mounted(){
            console.log("mounted");
    },
    beforeUpdate(){
            console.log("beforeUpdate");
    },
    updated(){
            console.log("updated");
    },
    beforeDestory(){
            console.log("beforeDestory");
    },
    destroyed(){
            console.log("destroyed");
    },
};
</script>