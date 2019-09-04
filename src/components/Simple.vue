<template>
  <div class="row">
    <div class="col-sm">
      <form>
        <div class="form-group">
          <label for="question">procurement_type</label>
          <select v-model="state.vehicles.vehicle1.procurement_type['2019-08']" class="form-control" id="question">
            <option value='crown'>crown</option>
            <option value='lease'>lease</option>
            <option value='private'>private</option>
          </select>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">travelling_to_usa</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio1" :value="true" v-model="state.vehicles.vehicle1.travelling_to_usa['2019-08']">
            <label class="form-check-label" for="inlineRadio1">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="inlineRadio2" :value="false" v-model="state.vehicles.vehicle1.travelling_to_usa['2019-08']">
            <label class="form-check-label" for="inlineRadio2">false</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">commercial_insurance_purchased?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="commercialInsurance" id="commercialInsuranceYes"  :value="true" v-model="state.vehicles.vehicle1.commercial_insurance_purchased['2019-08']">
            <label class="form-check-label" for="commercialInsuranceYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="commercialInsurance" id="commercialInsuranceNo"  :value="false" v-model="state.vehicles.vehicle1.commercial_insurance_purchased['2019-08']">
            <label class="form-check-label" for="commercialInsuranceNo">false</label>
          </div>
        </div>


        <!-- Start here -->


        <div class="form-group">
          <label for="exampleFormControlTextarea1">dtec_used?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="dtecUsed" id="dtecUsedYes"  :value="true" v-model="state.vehicles.vehicle1.dtec_used['2019-08']">
            <label class="form-check-label" for="dtecUsedYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="dtecUsed" id="dtecUsedNo"  :value="false" v-model="state.vehicles.vehicle1.dtec_used['2019-08']">
            <label class="form-check-label" for="dtecUsedNo">false</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">idtc_used?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="idtcUsed" id="idtcUsedYes"  :value="true" v-model="state.vehicles.vehicle1.idtc_used['2019-08']">
            <label class="form-check-label" for="idtcUsedYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="idtcUsed" id="idtcUsedNo"  :value="false" v-model="state.vehicles.vehicle1.idtc_used['2019-08']">
            <label class="form-check-label" for="idtcUsedNo">false</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">personal_card_used?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="personalCard" id="personalCardYes"  :value="true" v-model="state.vehicles.vehicle1.personal_card_used['2019-08']">
            <label class="form-check-label" for="personalCardYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="personalCard" id="personalCardNo"  :value="false" v-model="state.vehicles.vehicle1.personal_card_used['2019-08']">
            <label class="form-check-label" for="personalCardNo">false</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">personal_card_collision_damage_waiver?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="personalCardWithCoverage" id="personalCardWithCoverageYes"  :value="true" v-model="state.vehicles.vehicle1.personal_card_collision_damage_waiver['2019-08']">
            <label class="form-check-label" for="personalCardWithCoverageYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="personalCardWithCoverage" id="personalCardWithCoverageNo"  :value="false" v-model="state.vehicles.vehicle1.personal_card_collision_damage_waiver['2019-08']">
            <label class="form-check-label" for="personalCardWithCoverageNo">false</label>
          </div>
        </div>

        <!-- End here -->
        <div class="form-group">
          <label for="exampleFormControlTextarea1">government_approved_car_rental_suppliers?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="supplier" id="supplierYes" :value="true" v-model="state.vehicles.vehicle1.government_approved_car_rental_suppliers['2019-08']">
            <label class="form-check-label" for="supplierYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="supplier" id="supplierNo" :value="false" v-model="state.vehicles.vehicle1.government_approved_car_rental_suppliers['2019-08']">
            <label class="form-check-label" for="supplierNo">false</label>
          </div>
        </div>
        <div class="form-group">
          <label for="exampleFormControlTextarea1">basic_insurance_coverage?</label>
          <br>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="basicInsurance" id="basicInsuranceYes"  :value="true" v-model="state.vehicles.vehicle1.basic_insurance_coverage['2019-08']">
            <label class="form-check-label" for="basicInsuranceYes">true</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="basicInsurance" id="basicInsuranceNo"  :value="false" v-model="state.vehicles.vehicle1.basic_insurance_coverage['2019-08']">
            <label class="form-check-label" for="basicInsuranceNo">false</label>
          </div>
        </div>
        <button type="button" class="btn btn-primary" v-on:click="this.check">Check</button>
      </form>
    </div>
    <div class="col-sm">
      <ul class="list-group">
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', }">Vehicle is Insured</li>
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.collision_damage_waiver['2019-08'] : '', }">Collision Damage Waiver Coverage</li>
        <li class="list-group-item" v-bind:class="{ 'list-group-item-success': this.response.vehicles ? this.response.vehicles.vehicle1.vehicle_is_insured['2019-08'] : '', 'list-group-item-danger': this.response.vehicles ? !this.response.vehicles.vehicle1.public_liability_and_property_damage['2019-08'] : '', }">Public Liability and Property Damage Coverage</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  methods: {
    init: function () {
      // this.state = this.initial;
    },
    check: function() {
      if (this.state.vehicles.vehicle1.procurement_type['2019-08'] !== "") {
        this.ajaxRequest = true;
        this.$http.post('http://127.0.0.1:5001/calculate',
          JSON.stringify(this.state),
          function (data, status, request) {
            this.response = JSON.parse(data);
            this.ajaxRequest = false;
          }).then(response => {
            this.response = response.body;
          });
      } else {
        alert('Please select a procurement type.')
      }
    },
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
