<template>
<div class="container">
    
    <div class="row">
        <b-field label="Have you already picked out a home you want to purchase with no down payment?" class="col-lg-12 text-left" custom-class="is-large"><!-- (use the Google maps API we used before) -->
            
        </b-field>
                
        
    </div>
    <b-field class="col-lg-8 text-left">
        <b-radio v-model="radio" native-value="YES" >
            YES
        </b-radio>
    
    </b-field>
    <b-field class="col-lg-8 text-left">
        <b-radio v-model="radio" native-value="NO" >
            NO
        </b-radio>
    </b-field>

    <template v-if="radio === 'YES'">
        <!-- // address -->
        
        <b-field label="What is the address" class="col-lg-8 text-left mt-5"><!-- (use the Google maps API we used before) -->
            <vue-google-autocomplete
                ref="address"
                id="map"
                classname="form-control"
                placeholder="Please type your address"
                v-on:placechanged="getAddressData"
                country="us"
            >
            </vue-google-autocomplete>
        </b-field>
        
        
        <!-- // price -->
        
        <b-field label="What is the estimated purchase price?" class="col-lg-8 text-left mt-5">
            <b-input v-model="name"></b-input>
        </b-field>
    
        
        <!-- // purchase -->
        
        <b-field label="Do you already have a purchase REALTOR?" class="col-lg-8 text-left mt-5">
        </b-field>
        
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioREALTOR"
                native-value="YES">
                YES
            </b-radio>
        </b-field>
        
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioREALTOR"
                native-value="NO">
                NO
            </b-radio>
        </b-field>

        <!-- // annual  -->
        <b-field label="What is your annual household income?" class="col-lg-8 text-left mt-5">
            <b-input v-model="name"></b-input>
        </b-field>
    
        <!-- // own home -->
        <b-field label="Do you already own a home?" class="col-lg-8 text-left mt-5">
                
        </b-field>
        
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioHome"
                native-value="YES">
                YES
            </b-radio>
        </b-field>

        <template v-if="radioHome === 'YES'">
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioPrimaryHome"
                    native-value="YES">
                    Primary home
                </b-radio>
            </b-field>
            
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioPrimaryHome"
                    native-value="NO">
                    Investment home
                </b-radio>
            </b-field>
        </template>

        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioHome"
                native-value="NO">
                NO
            </b-radio>
        </b-field>
        
        <!--  veteran -->
        <b-field label="Are you a veteran?" class="col-lg-8 text-left mt-5">
        </b-field>
                    
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioVeteran"
                native-value="YES">
                YES
            </b-radio>
        </b-field>

        <template v-if="radioVeteran === 'YES'">

            <b-field label="Do you have a service related disability?" class="col-lg-8 text-left ml-5">
            </b-field>
            
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioDisability"
                    native-value="YES">
                    YES
                </b-radio>
            </b-field>

            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioDisability"
                    native-value="NO">
                    NO
                </b-radio>
            </b-field>
        </template>

        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioVeteran"
                native-value="NO">
                NO
            </b-radio>
        </b-field>
        
        <!-- firstname -->
        
        <b-field horizontal label="First name" class="col-lg-7 text-left mt-5">
            <b-input  v-model="firstname"></b-input>
        </b-field>
    
        <b-field horizontal label="Last name" class="col-lg-7 text-left">
            <b-input v-model="lastname"></b-input>
        </b-field>
    
        <!-- // phone number -->
        <b-field horizontal label="Phone number" class="col-lg-7 text-left">
            <b-input v-model="phonenumber"></b-input>
        </b-field>

        <!-- // email address -->
        <b-field horizontal label="Email address" class="col-lg-7 text-left">
            <b-input v-model="emailaddress"></b-input>
        </b-field>

    </template>

    <!-- //////////////// NO ///////////////// -->
    <template v-else-if="radio === 'NO'">

        <!-- county -->
        
        <b-field label="What county do you want to buy in?" class="col-lg-8 text-left mt-5">
            <dropdown></dropdown>
        </b-field>
        <!-- approximate purchase price -->

        <b-field label="How much is the approximate purchase price of the home you want to buy?" class="col-lg-8 text-left mt-5">
            <b-input v-model="emailaddress"></b-input>
        </b-field>

        <!-- // purchase realtor -->
        
        <b-field label="Do you already have a purchase REALTOR?" class="col-lg-8 text-left mt-5">
        </b-field>
    
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioREALTOR"
                native-value="YES">
                YES
            </b-radio>
        </b-field>
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioREALTOR"
                native-value="NO">
                NO
            </b-radio>
        </b-field>
        
        <!-- // annual  -->
        <b-field label="What is your annual household income?" class="col-lg-8 text-left mt-5">
            <b-input v-model="name"></b-input>
        </b-field>
    
        <!-- // own home -->
        <b-field label="Do you already own a home?" class="col-lg-8 text-left mt-5">
                
        </b-field>
                
    
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioHome"
                native-value="YES">
                YES
            </b-radio>
        </b-field>

        <template v-if="radioHome === 'YES'">
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioPrimaryHome"
                    native-value="YES">
                    Primary home
                </b-radio>
            </b-field>
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioPrimaryHome"
                    native-value="NO">
                    Investment home
                </b-radio>
            </b-field>
        </template>

        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioHome"
                native-value="NO">
                NO
            </b-radio>
        </b-field>

        <!--  veteran -->
        
        <b-field label="Are you a veteran?" class="col-lg-8 text-left mt-5">
                
        </b-field>
                
        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioVeteran"
                native-value="YES">
                YES
            </b-radio>
        </b-field>

        <template v-if="radioVeteran === 'YES'">

            <b-field label="Do you have a service related disability?" class="col-lg-8 text-left ml-5">
                    
            </b-field>

            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioDisability"
                    native-value="YES">
                    YES
                </b-radio>
            </b-field>
            <b-field class="col-lg-8 text-left ml-5">
                <b-radio v-model="radioDisability"
                    native-value="NO">
                    NO
                </b-radio>
            </b-field>
        </template>

        <b-field class="col-lg-8 text-left">
            <b-radio v-model="radioVeteran"
                native-value="NO">
                NO
            </b-radio>
        </b-field>

        
        
        <!-- firstname -->
        <b-field horizontal label="First name" class="col-lg-7 text-left mt-5">
            <b-input  v-model="firstname"></b-input>
        </b-field>
    
        <b-field horizontal label="Last name" class="col-lg-7 text-left">
            <b-input v-model="lastname"></b-input>
        </b-field>
    
        <!-- // phone number -->
        <b-field horizontal label="Phone number" class="col-lg-7 text-left">
            <b-input v-model="phonenumber"></b-input>
        </b-field>

        <!-- // email address -->
        <b-field horizontal label="Email address" class="col-lg-7 text-left">
        <b-input v-model="emailaddress"></b-input>
        </b-field>
    </template>
    <template >
        
    </template>

    
    <b-message type="is-success" class="col-lg-8" v-if="radio === 'none'">
        To continue, please select above option
    </b-message>
    <b-field class="col-lg-7 text-right" v-else>
        <button type="submit" class="button" @click="postPost">Submit</button>
    </b-field>

        
</div>
</template>

<script>
import DropdownCounty from './DropdownCounty'
import VueGoogleAutocomplete from 'vue-google-autocomplete'
import axios from 'axios'
export default {
  name: 'Questions',
  data() {
        return {
            radio: 'none',
            radioREALTOR: 'none',
            radioHome: 'none',
            radioPrimaryHome: 'none',
            radioVeteran : 'none',
            radioDisability : "none",
            address: '',
            postBody: '',
            errors: [],
            
        }
    },
    components: {
        dropdown: DropdownCounty,
        VueGoogleAutocomplete
    },
    methods: {
        /**
        * When the location found
        * @param {Object} addressData Data of the found location
        * @param {Object} placeResultData PlaceResult object
        * @param {String} id Input container ID
        */
        getAddressData: function (addressData, placeResultData, id) {
            this.address = addressData;
        },
        alert() {
            this.$dialog.alert('Searching for programs. Make it look busy then inform them that a licensed, zero down payment expert will be reaching out to review their options')
            
        },
        // Pushes posts to the server when called.
        postPost() {
            this.postBody = this.address
            axios.post(`http://jsonplaceholder.typicode.com/posts`, {
            body: this.postBody
            })
            .then(response => {
                this.alert()

            })
            .catch(e => {
            this.errors.push(e)
            })

        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.button{
  background: #50d8af;
  border: 0;
  border-radius: 3px;
  color: #fff;
  transition: 0.4s;
  cursor: pointer;
}
</style>
