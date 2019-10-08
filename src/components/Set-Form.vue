<template>
<div class="container">
  <section>
    <h5>Set up Form</h5>
    <hr />
    <div class="row">
      <div class="col-12">
        <h6>Estate Agent Details</h6>
        <div class="cardMain">
          <ul class="top-list">
            <li><input name="estate_agent_name" type="input" placeholder="Estate Agent name" v-model="estate['name']"></li>
            <li><textarea name="estate_agent_address" placeholder="Head Office" v-model="estate['address']"></textarea></li>
            <li><input name="estate_agent_postcode" type="input" placeholder="Postcode" v-model="estate['postcode']"></li>
            <li><input name="estate_agent_phone" type="input" placeholder="Phone number" v-model="estate['phone']"></li>
            <li><input name="estate_agent_info" type="input" placeholder="Email" v-model="estate['email']"></li>
          </ul>
        </div><!-- End Card Main -->
      </div><!-- End Col 12 -->
      <div class="col-12">
        <h6>Group AML Officer</h6>
        <div class="cardMain">
          <ul class="top-list">
            <li><input name="aml_name" type="input" placeholder="Name" v-model="aml['name']"></li>
            <li><input name="aml_phone" type="input" placeholder="Phone number" v-model="aml['phone']"></li>
            <li><input name="aml_email" type="input" placeholder="Email" v-model="aml['email']"></li>
            <li><textarea name="aml_info" placeholder="Additional information" v-model="aml['info']"></textarea></li>
          </ul>
        </div><!-- End Card Main -->
      </div><!-- End Col 12 -->
      <div class="col-12">
        <h6>Point of contact for accounts</h6>
        <div class="cardMain">
          <ul class="top-list">
            <li><input name="poc_name" type="input" placeholder="Name" v-model="poc['name']"></li>
            <li><input name="poc_phone" type="input" placeholder="Phone number" v-model="poc['phone']"></li>
            <li><input name="poc_email" type="input" placeholder="Email" v-model="poc['email']"></li>
            <li><textarea name="poc_info" placeholder="Additional information" v-model="poc['info']"></textarea></li>
          </ul>
        </div><!-- End Card Main -->
      </div><!-- End Col 12 -->
      <div class="col-12">
        <h6>MI Reports Required</h6>
        <div class="cardMI">
          <div class="d-flex">
            <p style="width: 30%">Branch League Report:</p>
            <input type="radio" value="yes" v-model="reports['branchLeagueReport']"><label>Yes</label>
            <input type="radio" value="no" v-model="reports['branchLeagueReport']"><label>No</label>
            <transition name="slide">
              <div v-show="reports['branchLeagueReport'] === 'yes'">
                <p style="color: #4AC948; padding-left: 15px;"><b>Branch League Report</b> <i class="fas fa-check-circle"></i></p>
              </div>
            </transition>
          </div><!-- End d-flex -->
          <div class="d-flex">
            <p style="width: 30%">Negotiator League Report: </p>
            <input type="radio" value="yes" v-model="reports['negotiatorLeagueReport']"><label>Yes</label>
            <input type="radio" value="no" v-model="reports['negotiatorLeagueReport']"><label>No</label>
            <transition name="slide">
              <div v-show="reports['negotiatorLeagueReport'] === 'yes'">
                <p style="color: #4AC948; padding-left: 15px;"><b>Negotiator League Report</b>&nbsp; <i class="fas fa-check-circle"></i></p>
              </div>
            </transition>
          </div><!-- End d-flex -->
          <div class="d-flex">
            <p style="width: 30%">Uplift League Report:</p>
            <input type="radio" value="yes" v-model="reports['upliftLeagueReport']"><label>Yes</label>
            <input type="radio" value="no" v-model="reports['upliftLeagueReport']"><label>No</label>
            <transition name="slide">
              <div v-show="reports['upliftLeagueReport'] === 'yes'">
                <p style="color: #4AC948; padding-left: 15px;"><b>Uplift League Report</b> <i class="fas fa-check-circle"></i></p>
              </div>
            </transition>
          </div><!-- End d-flex -->
          <div class="d-flex">
            <p style="width: 30%">Zero List Report:</p>
            <input type="radio" value="yes" v-model="reports['zeroListReport']"><label>Yes</label>
            <input type="radio" value="no" v-model="reports['zeroListReport']"><label>No</label>
            <transition name="slide">
              <div v-show="reports['zeroListReport'] === 'yes'">
                <p style="color: #4AC948; padding-left: 15px;"><b>Zero List Report</b> <i class="fas fa-check-circle"></i></p>
              </div>
            </transition>
          </div><!-- End d-flex -->
        </div><!-- End Card Main -->
      </div><!-- End Col 12 -->
      <div class="col-12">
        <h6>Add a Branch</h6>
        <div class="addNegotiatorCard">
          <div class="dunno">
            <transition name="slide">
              <div class="top-list">
                <div v-for="(branch, index) in branches" class=" padding">
                  <p>Branch details</p>
                  <input type="input" placeholder="Branch name" v-model="branch.one">
                  <input type="input" placeholder="Branch address" v-model="branch.two">
                  <input type="input" placeholder="Branch postcode" v-model="branch.three">
                  <input type="input" placeholder="Branch email" v-model="branch.four">
                  <input type="input" placeholder=" Branch phone number" v-model="branch.five">
                  <input type="input" placeholder=" Branch Manager" v-model="branch.six">
                  <textarea style="margin-top: 15px;" placeholder="Branch Manager Details"></textarea>
                  <div class="top-list">
                    <div v-for="(negotiator, index) in negotiators" style=" margin-top: 25px; background: #FAFAFA; padding: 15px; border-radius: 15px;">
                      <p>Negotiator details</p>
                      <input type="input" placeholder="Name" v-model="negotiator.one">
                      <input type="input" placeholder="Job Title" v-model="negotiator.two">
                      <input type="input" placeholder="Email" v-model="negotiator.three">
                      <input type="input" placeholder="Phone Number" v-model="negotiator.four">
                      <br />
                      <button style="margin-top: 15px" @click="deleteNegotiator(index)" class="buttonMain">Delete Negotiator</button>
                    </div>
                  </div>
                  <div class="d-flex">
                    <button type="button" class="ml-auto buttonMain" style="margin-right: 15px; margin-top: 15px;" @click="addNegotiator">Add a negotiator</button>
                  </div>
                  <button style="margin-top: 10px;" @click="deleteBranches(index)" class="buttonMain">Delete Branch</button>
                  <hr />
                </div>
              </div>
            </transition>
          </div>
          <div class="d-flex">
            <button type="button" class="ml-auto buttonMain" style="margin-right: 15px; margin-bottom: 15px;" @click="addBranches">Add a Branch</button>
          </div>
        </div><!-- End Card Main -->
      </div><!-- End Col 12 -->
    </div><!-- End row -->
    <div class="d-flex">
      <button type="button" class="ml-auto buttonMain" style="margin-bottom: 15px;" v-model="saveButton['save']">Save</button>
    </div>
  </section>
</div><!-- End Container -->
</template>

<script>
export default {
  name: 'set-form',
  components: {},
  data() {
    return {
      estate: {
        'name': "",
        'address': "",
        'postcode': "",
        'phone': "",
        'email': "",
      },
      branch: {
        'name': "",
        'address': "",
        'postcode': "",
        'phone': "",
        'email': "",
      },
      manager: {
        'name': "",
        'phone': "",
        'email': "",
        'info': "",
      },
      aml: {
        'name': "",
        'phone': "",
        'email': "",
        'info': "",
      },
      poc: {
        'name': "",
        'phone': "",
        'email': "",
        'info': "",
      },
      pocmanager: {
        'name': "",
        'phone': "",
        'email': "",
        'info': "",
      },
      saveButton: {
        'save': "",
      },
      reports: {
        'branchLeagueReport': false,
        'negotiatorLeagueReport': false,
        'upliftLeagueReport': false,
        'zeroListReport': false,
      },
      negotiators: [],
      branches: [],
    }
  },
  methods: {
    addNegotiator() {
      this.negotiators.push({
        one: '',
        two: ''
      })
    },
    deleteNegotiator(index) {
      this.negotiators.splice(index, 1)
    },
    addBranches() {
      this.branches.push({
        one: '',
        two: ''
      })
    },
    deleteBranches(index) {
      this.branches.splice(index, 1)
    },
  }
}
</script>

<style lang="scss" scoped>
$muted: #888;
$light-grey: #eee;
$blue: #016BA8;
section {
    color: $muted;
    margin-top: 25px;

    h6 {
        font-size: 18px;
    }
    h5 {
        font-size: 24px;
    }
    .sub-heading {
        padding: 7.5px 0;
    }
    .fa-check-circle {
        color: #4AC948;
    }
    input {
        border: none;
        border-bottom: 1px solid $light-grey;
        padding: 5px 0;
        color: $muted;
        background: none;
        &:focus {
            border: none;
            outline: none;
        }
    }
    .top-list {
        li {
            padding: 5px 0;
            list-style: none;
        }

    }
}

.cardMain {
    background: #fff;
    margin: 20px 0;
    padding: 0.1rem;
    border-radius: 10px;
    box-shadow: 0 0 5px 3px rgba(0,0,0,0.1);
    ul {
        list-style: none;
    }
    input {
        width: 90%;
        margin: 7.5px 0;
    }
    textarea {
        width: 90%;
        background: #FAFAFA;
        border: none;
        padding: 10px;
        height: 100px;
        &:focus {
            border: none;
            outline: none;
        }
    }
}

.addNegotiatorCard {
    background: #fff;
    margin: 20px 0;
    padding: 0.1rem;
    border-radius: 10px;
    box-shadow: 0 0 5px 3px rgba(0,0,0,0.1);
    ul {
        list-style: none;
    }
    input {
        width: 90%;
        margin: 7.5px 0;
    }
    ul {
        padding-left: 20px;
        width: 90%;
        /*background: #fafafa;*/
        margin: 15px;
    }
    .dunno {
        margin-top: 15px;
    }
}

.buttonMain {
    background: $blue;
    color: #fff;
    padding: 0.3rem 0.5rem;
    border-radius: 0.4rem;
    font-weight: light;
    font-size: 12px;
    letter-spacing: 2px;
    border: none;
    cursor: pointer;
    outline: none;
}

.slide-enter-active {
    transition-duration: 1s;
    transition-timing-function: ease-in;
}

.slide-leave-active {
    transition-duration: 0.3s;
    transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
}

.slide-enter-to,
.slide-leave {
    max-height: 100px;
    overflow: hidden;
}

.slide-enter,
.slide-leave-to {
    overflow: hidden;
    max-height: 0;
}

.padding {
    padding: 1rem;
}

textarea {
    width: 90%;
    background: #FAFAFA;
    border: none;
    padding: 10px;
    height: 100px;
    &:focus {
        border: none;
        outline: none;
    }
}

.cardMI {
    background: #fff;
    margin: 20px 0;
    padding: 1rem;
    border-radius: 10px;
    box-shadow: 0 0 5px 3px rgba(0,0,0,0.1);
    .fa-check-circle {
        color: #4AC948;
    }

}

input[type="radio"]{
  margin: 7px;
}
</style>
