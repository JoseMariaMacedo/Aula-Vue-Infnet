<template>
    <div>
            <h1>{{ name_store || "My store" }}</h1>
            <h2 v-html="subTittle"></h2>

            <button
                @click="insert = !insert">Inserir</button>
            <div v-show="insert">
                <input type="text"
                @keyup.enter = "item.push ({ ...newItem })"
                v-model = "newItem.product">

                <strong>Priority:</strong>
                <label>
                    <input type="radio" v-model="newItem.priority" value="high">High
                </label>

                <label>
                    <input type="radio" v-model="newItem.priority" value="low">Low
                </label>

                <label>
                    <strong>Color:</strong>
                    <select v-model="newItem.color">
                        <option value="black">Black</option>
                        <option value="blue">Blue</option>
                        <option value="Pink">Pink</option>
                    </select>
                </label>

                <label>
                    <strong>Gift</strong>
                    <input type="checkbox" v-model="newItem.Gift">
                    Is a Gift?
                </label>

                <label>
                    <strong>Complements</strong>
                    <input type="checkbox" v-model="newItem.complements" value="giftcard">
                    Gift card?
                    <input type="checkbox" v-model="newItem.complements" value="tracking">
                    Tracking?
                </label>

                <br>
                <button
                    :disabled="newItem.product.length < 3 "
                    @click="items.push({ ...newItem })">
                    Save item
                </button>

            </div>
            <h3>items
                <span v-show="items.length > 0">
                    {{ items.length }}
                </span>    
            </h3>

            <p v-if="items.length === 0 ">No items</p>
            <div v-else-if="items.length === 1 ">1 Item</div>
            <span v-else>{{ items.length }} Items </span>

            <ul>
                <li
                    v-for="item in items"
                    :key="item.id">
                    <img v-bind="item.img" width="56">
                    {{ item.product }}
                    {{ item.price }}
                </li>
            </ul>
    </div>
</template>

<script>
    export default {
         name: 'Shopping',
         props: {
          name_store: String,
        },
        data(){
            return{
                subTitle: "<strong>Mult</strong> Shopping",
                insert: false,
                newItem:{
                    product: '',
                    priority: 'low',
                    color: 'black',
                    gift: false,
                    complements: [],
                },
                items: [
                    {id: 1, price: 60.0, product: 'chapeu'},
                    {id: 2, price: 55.93, product: 'jogo'},
                    {id: 3, price: 21.32, product: 'caneca'},
                ]
            }

        }
     
    
    }
</script>
<style scoped>
    strong, label{
        margin: 10px auto;
        display: block;
    }
    h3{
        margin: 40px 0 0;

    }
    ul{
        list-style-type: none;
        padding: 0;

    }
    li{
        display: block;
        margin: 10px 10px;
        font-size: x-large;
    }
    a{
        color: aquamarine;
    }
</style>