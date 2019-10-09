<template>
  <div class="row">
    <div class="col-sm">
      <form>
        <div class="form-group">
          <label for="question">How is the vehicle to be acquired?</label>
          <select v-model="state.vehicles.vehicle1.procurement_type['2019-08']" class="form-control" id="question" v-on:change="init">
            <option value='crown'>Crown Owned</option>
            <option value='lease'>Leased</option>
            <option value='private'>Privately Owned</option>
          </select>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">Is the vehicle travelling to the USA?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" :value="true" v-model="state.vehicles.vehicle1.travelling_to_usa['2019-08']">
            <label class="form-check-label" for="inlineRadio1">Yes</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" :value="false" v-model="state.vehicles.vehicle1.travelling_to_usa['2019-08']">
            <label class="form-check-label" for="inlineRadio2">No</label>
          </div>
        </div>
        <div v-if="state.vehicles.vehicle1.travelling_to_usa['2019-08']" class="form-group">
          <label for="exampleFormControlTextarea1">Has international commercial insurance been purchased?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="commercialInsurance" id="commercialInsuranceYes"  :value="true" v-model="state.vehicles.vehicle1.commercial_insurance_purchased['2019-08']">
            <label class="form-check-label" for="commercialInsuranceYes">Yes</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="commercialInsurance" id="commercialInsuranceNo"  :value="false" v-model="state.vehicles.vehicle1.commercial_insurance_purchased['2019-08']">
            <label class="form-check-label" for="commercialInsuranceNo">No</label>
          </div>
        </div>

        <div v-if="state.vehicles.vehicle1.procurement_type['2019-08'] === 'lease'" class="form-group">
          <label for="question">What was the payment method?</label>
          <select class="form-control" id="question" v-on:change="setPaymentMethod" v-model="paymentMethod">
            <option value='dtec'>Departmental Travel Expense Card</option>
            <option value='idtc'>Individual Designated Travel Card</option>
            <option value='pcc'>Personal Credit Card</option>
            <option value='pccwc'>Personal Credit Card with Collision Damage Waiver Coverage</option>
          </select>
        </div>
        <div v-if="state.vehicles.vehicle1.procurement_type['2019-08'] === 'lease'" class="form-group">
          <label for="exampleFormControlTextarea1">Did you use a government approved car rental supplier?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="supplier" id="supplierYes" :value="true" v-model="state.vehicles.vehicle1.government_approved_car_rental_suppliers['2019-08']">
            <label class="form-check-label" for="supplierYes">Yes</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="supplier" id="supplierNo" :value="false" v-model="state.vehicles.vehicle1.government_approved_car_rental_suppliers['2019-08']">
            <label class="form-check-label" for="supplierNo">No</label>
          </div>
        </div>
        <div v-if="state.vehicles.vehicle1.procurement_type['2019-08'] === 'private'" class="form-group">
          <label for="exampleFormControlTextarea1">Do you have basic insurance coverage, including the minimum Public Liability and Property Damage coverage required by the province/territory of registration of the vehicle
?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="basicInsurance" id="basicInsuranceYes"  :value="true" v-model="state.vehicles.vehicle1.basic_insurance_coverage['2019-08']">
            <label class="form-check-label" for="basicInsuranceYes">Yes</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="basicInsurance" id="basicInsuranceNo"  :value="false" v-model="state.vehicles.vehicle1.basic_insurance_coverage['2019-08']">
            <label class="form-check-label" for="basicInsuranceNo">No</label>
          </div>
        </div>
        <button type="button" class="btn btn-primary" v-on:click="this.check">Check</button>
      </form>
    </div>
    <div class="col-sm">
      <ul class="list-group">
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', }">Vehicle is Insured</li>
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.collision_damage_waiver['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.collision_damage_waiver['2019-08'] : '', }">Collision Damage Waiver Coverage</li>
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.public_liability_and_property_damage['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.public_liability_and_property_damage['2019-08'] : '', }">Public Liability and Property Damage Coverage</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  methods: {
    init: function () {
      if (this.state.vehicles.vehicle1.procurement_type['2019-08'] === "") {
        this.state = this.initial;
      }
      
    },
    check: function() {
      this.ajaxRequest = true;
      this.$http.post('https://rac-travel-api.herokuapp.com/calculate',
        JSON.stringify(this.state),
        function (data, status, request) {
          this.response = JSON.parse(data);
          this.ajaxRequest = false;
        }).then(response => {
          this.response = response.body;
        });
    },
    setPaymentMethod: function () {
      this.state.vehicles.vehicle1.dtec_used['2019-08']  = false;
      this.state.vehicles.vehicle1.idtc_used['2019-08'] = false;
      this.state.vehicles.vehicle1.personal_card_used['2019-08'] = false;
      this.state.vehicles.vehicle1.personal_card_collision_damage_waiver['2019-08'] = false;
      switch(this.paymentMethod) {
        case 'dtec':
          this.state.vehicles.vehicle1.dtec_used['2019-08']  = true;
          break;
        case 'idtc':
          this.state.vehicles.vehicle1.idtc_used['2019-08'] = true;
          break;
        case 'pcc':
          this.state.vehicles.vehicle1.personal_card_used['2019-08'] = true;
          break;
        case 'pccwc':
          this.state.vehicles.vehicle1.personal_card_collision_damage_waiver['2019-08'] = true;
          break;
        default:
          // code block
      }
    }
  },
  data: function() {
    return {
      paymentMethod: '',
      response: {},
      initial: {
        persons: {
          parent1: {}
        },
        vehicles: {
          vehicle1: {
            procurement_type: {
              '2019-08': null
            },
            travelling_to_usa: {
              '2019-08': null
            },
            travelling_outside_of_canada: {
              '2019-08': null
            },
            commercial_insurance_purchased: {
              '2019-08': null
            },
            vehicle_is_insured: {
              '2019-08': null
            },
            dtec_used: {
              '2019-08': null
            },
            idtc_used: {
              '2019-08': null
            },
            personal_card_used: {
              '2019-08': null
            },
            personal_card_collision_damage_waiver: {
              '2019-08': null
            },
            government_approved_car_rental_suppliers: {
              '2019-08': null
            },
            public_liability_and_property_damage_purchased: {
              '2019-08': null
            },
            basic_insurance_coverage: {
              '2019-08': null
            },
            collision_damage_waiver: {
              '2019-08': null
            },
            public_liability_and_property_damage: {
              '2019-08': null
            }
          }
        }
      }, 
      state: {
        persons: {
          parent1: {}
        },
        vehicles: {
          vehicle1: {
            procurement_type: {
              '2019-08': ''
            },
            travelling_to_usa: {
              '2019-08': null
            },
            travelling_outside_of_canada: {
              '2019-08': null
            },
            commercial_insurance_purchased: {
              '2019-08': null
            },
            vehicle_is_insured: {
              '2019-08': null
            },
            dtec_used: {
              '2019-08': null
            },
            idtc_used: {
              '2019-08': null
            },
            personal_card_used: {
              '2019-08': null
            },
            personal_card_collision_damage_waiver: {
              '2019-08': null
            },
            government_approved_car_rental_suppliers: {
              '2019-08': null
            },
            public_liability_and_property_damage_purchased: {
              '2019-08': null
            },
            basic_insurance_coverage: {
              '2019-08': null
            },
            collision_damage_waiver: {
              '2019-08': null
            },
            public_liability_and_property_damage: {
              '2019-08': null
            }
          }
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.good {
  color: green;
}

.bad {
  color: red;
}
</style>
