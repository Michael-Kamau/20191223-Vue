<template>
    <!-- Your HTML goes here -->
    <div class="home">
        <h1>Welcome</h1>

        <div>
            <table>
                <thead>
                <tr>
                    <th>Product</th>
                    <th>Amount</th>
                </tr>
                </thead>
                <tr v-for="product in products" :key="product.amount">
                    <td>{{product.name}}</td>
                    <td>{{product.amount}}</td>
                </tr>
            </table>
        </div>
        <h2>Calculate Commission</h2>
        <div class="form-group">
            <label for="amount"><b>Enter amount: &nbsp;</b></label>
            <input class="form-control" name="teacher" v-model="amount">(message below is determined by the amount on this field)
            <p v-if="amount > 50000"> <b>Note:</b>Congratulations on your good work!!</p>
            <p v-else> <b>Note:</b>Put more effort</p>
        </div>

        <div v-bind:class="classObject">
            <p>Commission:&nbsp; {{amount*0.035}}</p>
        </div>
        <div>
            <form action="/action_page.php">
                <label for="fname">Product</label>
                <input type="text" id="product" name="product" placeholder="Product" v-model="details.product">

                <label for="lname">Amount</label>
                <input type="text" id="amount" name="amount" placeholder="amount" v-model="details.amount">

                <label for="interest">Interest</label>
                <input type="text" id="interest" name="interest" placeholder="Interest." v-model="details.interest">

                <input type="submit" value="Submit" v-on:click="methods.submit()">
            </form>
        </div>


    </div>
</template>

<script>
    export default {
        name: 'Index',
        active: true,
        data() {
            return {
                amount: 1000,

                classObject: {
                    active: true,
                    'text-danger': false
                },
                products: [
                    {name: 'Mazda', amount: 150000},
                    {name: 'Toyota', amount: 120000},
                    {name: 'Nissan', amount: 180000},
                    {name: 'Subaru', amount: 220000},

                ],
                methods: {
                    submit: function () {
                        alert("Are you sure you want to submit the form")

                    }
                },
                details: {}
            }
        }
    }


</script>

<style>

    .active {
        color: blue;
    }

    label{
        padding:10px;
    }

    table, td, th {
        border: 1px solid #ddd;
        text-align: left;
    }

    table {
        border-collapse: collapse;
        width: 50%;
    }

    th, td {
        padding: 15px;
    }

</style>
