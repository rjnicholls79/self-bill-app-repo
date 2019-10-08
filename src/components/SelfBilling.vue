<template>
  <div class="outer_div container">
    <section>
      <h5>Self Billing Form</h5>
      <hr/>
      <h6>This is an agreement to a self-billing procedure between:</h6>
      <div class="cardMain">
      <ul class="top-list">
        <li>Lifetime Legal Ltd	</li>
        <li>VAT Number:  189 5024 79</li>
        <li><input type="input" name="estate_agent" placeholder="Estate Agent Name" v-model="estateAgentName['name']"></li>
        <li><input type="input" name="vat_number" placeholder="VAT Number:" v-model="vatNumber['number']"></li>
      </ul>
    </div>
      <hr/>
      <h6 class="sub-heading"><i class="fas fa-check-circle"></i>&nbsp;Lifetime Legal Ltd Agrees:</h6>
      <div class="cardMain">
        <ol>
          <li>To issue self-billed invoices for all fees due to you until the date when our agreement ends</li>
          <li>To create self-billed invoices showing your name, address & VAT registration number (where applicable), together with all the other details that constitute a full VAT invoice.</li>
          <li>To provide a new self-billing agreement in the event our VAT registration number changes</li>
          <li>To inform you if the issue of self-billed invoices will be outsourced to a third party.</li>
        </ol>
      </div>
      <hr/>
      <h6 class="sub-heading"><i class="fas fa-check-circle"></i>&nbsp;You Agree:</h6>
      <div class="cardMain">
        <ol>
          <li>To accept invoices raised by Lifetime Legal on your behalf until the date when our agreement ends.</li>
          <li>Not to raise sales invoices for the transactions covered by this agreement.</li>
          <li>To notify Lifetime Legal immediately if you:
            <ol>
              <li>Change your VAT registration number, or</li>
              <li>Cease to be VAT registered, or</li>
              <li>Sell the business, or part of the business.</li>
            </ol>
          </li>
        </ol>
      </div>
      <hr/>
      <h6 class="sub-heading">Your Bank Details</h6>
      <div class="cardMain">
        <ul>
          <li><input type="input" name="bank_name" placeholder="Bank Account Name" v-model="bankAccountName['bank-name']"></li>
          <li><input type="input" name="bank_account_number" placeholder="Bank Account Number" v-model="bankAccountNumber['bank-account-number']"></li>
          <li><input type="input" name="bank_sort_code" placeholder="Sort Code" v-model="bankSortCode['bank-sort-code']"></li>
          <li><input type="input" name="billing_address" placeholder="Billing address" v-model="billingAddress['billing-address']"></li>
        </ul>
      </div>
      <hr/>
      <div class="row">
        <div class="col-6">
          <h6 class="sub-heading">Signature:</h6>
          <div class="cardMain">
            <div class="row">
              <div class="col-md-12">
                <h6>E-Signature</h6>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <canvas id="sig-canvas">
                  Get a better browser, bro.
                </canvas>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <button class="btn btn-primary" id="sig-submitBtn">Submit Signature</button>
                <button class="btn btn-default" id="sig-clearBtn">Clear Signature</button>
              </div>
            </div>
            <br/>
            <div class="row">
              <div class="col-md-12">
                <textarea id="sig-dataUrl" class="form-control" rows="5">Data URL for your signature will go here!</textarea>
              </div>
            </div>
            <br/>
            <div class="row">
              <div class="col-md-12">
                <img id="sig-image" src="" alt="Your signature will go here!"/>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <input type="input" placeholder="Print Name">
                <p><b>On Behalf of:</b></p>
                <p>Lifetime Legal Ltd</p>
                <input type="date"/>
              </div>
            </div>
          </div><!-- End Card Main -->
        </div><!-- End col -->
        <div class="col-6">
          <h6 class="sub-heading">Signature:</h6>
          <div class="cardMain">
            <div class="row">
              <div class="col-md-12">
                <h6>E-Signature</h6>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <canvas id="ig-canvas">
                  Get a better browser, bro.
                </canvas>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <button class="btn btn-primary" id="ig-submitBtn">Submit Signature</button>
                <button class="btn btn-default" id="ig-clearBtn">Clear Signature</button>
              </div>
            </div>
            <br/>
            <div class="row">
              <div class="col-md-12">
                <textarea id="ig-dataUrl" class="form-control" rows="5">Data URL for your signature will go here!</textarea>
              </div>
            </div>
            <br/>
            <div class="row">
              <div class="col-md-12">
                <img id="ig-image" src="src/assets/logo.png" alt="Your signature will go here!"/>
              </div>
            </div>
            <div class="row">
              <div class="col-md-12">
                <input type="input" placeholder="Print Name">
                <p><b>On Behalf of:</b></p>
                <p>Lifetime Legal Ltd</p>
                <input type="date"/>
              </div>
            </div>
          </div><!-- End Card Main -->
        </div><!-- End col -->
      </div><!-- End Row -->
      <div class="d-flex">
      <button type="button" class="ml-auto buttonMain" style="margin-bottom: 15px;" v-model="saveButton['save']">Save</button>
    </div>
    </section>
  </div><!-- End Outer Div -->
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      saveButton: {
        'save': "",
      },
      estateAgentName:{
        'name':"",
      },
      vatNumber:{
        'number':"",
      },
      bankAccountName:{
        'bank-name':"",
      },
      bankAccountNumber:{
        'bank-account-number':"",
      },
      bankSortCode:{
        'bank-sort-code':"",
      },
      billingAddress:{
        'billing-address':"",
      }
    }
  },
  mounted(){
    (function() {
  window.requestAnimFrame = (function(callback) {
    return window.requestAnimationFrame ||
      window.webkitRequestAnimationFrame ||
      window.mozRequestAnimationFrame ||
      window.oRequestAnimationFrame ||
      window.msRequestAnimaitonFrame ||
      function(callback) {
        window.setTimeout(callback, 1000 / 60);
      };
  })();

  var canvas = document.getElementById("sig-canvas");
  var ctx = canvas.getContext("2d");
  ctx.strokeStyle = "#222222";
  ctx.lineWidth = 4;

  var drawing = false;
  var mousePos = {
    x: 0,
    y: 0
  };
  var lastPos = mousePos;

  canvas.addEventListener("mousedown", function(e) {
    drawing = true;
    lastPos = getMousePos(canvas, e);
  }, false);

  canvas.addEventListener("mouseup", function(e) {
    drawing = false;
  }, false);

  canvas.addEventListener("mousemove", function(e) {
    mousePos = getMousePos(canvas, e);
  }, false);

  // Add touch event support for mobile
  canvas.addEventListener("touchstart", function(e) {

  }, false);

  canvas.addEventListener("touchmove", function(e) {
    var touch = e.touches[0];
    var me = new MouseEvent("mousemove", {
      clientX: touch.clientX,
      clientY: touch.clientY
    });
    canvas.dispatchEvent(me);
  }, false);

  canvas.addEventListener("touchstart", function(e) {
    mousePos = getTouchPos(canvas, e);
    var touch = e.touches[0];
    var me = new MouseEvent("mousedown", {
      clientX: touch.clientX,
      clientY: touch.clientY
    });
    canvas.dispatchEvent(me);
  }, false);

  canvas.addEventListener("touchend", function(e) {
    var me = new MouseEvent("mouseup", {});
    canvas.dispatchEvent(me);
  }, false);

  function getMousePos(canvasDom, mouseEvent) {
    var rect = canvasDom.getBoundingClientRect();
    return {
      x: mouseEvent.clientX - rect.left,
      y: mouseEvent.clientY - rect.top
    }
  }

  function getTouchPos(canvasDom, touchEvent) {
    var rect = canvasDom.getBoundingClientRect();
    return {
      x: touchEvent.touches[0].clientX - rect.left,
      y: touchEvent.touches[0].clientY - rect.top
    }
  }

  function renderCanvas() {
    if (drawing) {
      ctx.moveTo(lastPos.x, lastPos.y);
      ctx.lineTo(mousePos.x, mousePos.y);
      ctx.stroke();
      lastPos = mousePos;
    }
  }

  // Prevent scrolling when touching the canvas
  document.body.addEventListener("touchstart", function(e) {
    if (e.target == canvas) {
      e.preventDefault();
    }
  }, false);
  document.body.addEventListener("touchend", function(e) {
    if (e.target == canvas) {
      e.preventDefault();
    }
  }, false);
  document.body.addEventListener("touchmove", function(e) {
    if (e.target == canvas) {
      e.preventDefault();
    }
  }, false);

  (function drawLoop() {
    requestAnimFrame(drawLoop);
    renderCanvas();
  })();

  function clearCanvas() {
    canvas.width = canvas.width;
  }

  // Set up the UI
  var sigText = document.getElementById("sig-dataUrl");
  var sigImage = document.getElementById("sig-image");
  var clearBtn = document.getElementById("sig-clearBtn");
  var submitBtn = document.getElementById("sig-submitBtn");
  clearBtn.addEventListener("click", function(e) {
    clearCanvas();
    sigText.innerHTML = "Data URL for your signature will go here!";
    sigImage.setAttribute("src", "");
  }, false);
  submitBtn.addEventListener("click", function(e) {
    var dataUrl = canvas.toDataURL();
    sigText.innerHTML = dataUrl;
    sigImage.setAttribute("src", dataUrl);
  }, false);

})();

//SECOND ONE

(function() {
window.requestAnimFrame = (function(callback) {
return window.requestAnimationFrame ||
  window.webkitRequestAnimationFrame ||
  window.mozRequestAnimationFrame ||
  window.oRequestAnimationFrame ||
  window.msRequestAnimaitonFrame ||
  function(callback) {
    window.setTimeout(callback, 1000 / 60);
  };
})();

var canvas = document.getElementById("ig-canvas");
var ctx = canvas.getContext("2d");
ctx.strokeStyle = "#222222";
ctx.lineWidth = 4;

var drawing = false;
var mousePos = {
x: 0,
y: 0
};
var lastPos = mousePos;

canvas.addEventListener("mousedown", function(e) {
drawing = true;
lastPos = getMousePos(canvas, e);
}, false);

canvas.addEventListener("mouseup", function(e) {
drawing = false;
}, false);

canvas.addEventListener("mousemove", function(e) {
mousePos = getMousePos(canvas, e);
}, false);

// Add touch event support for mobile
canvas.addEventListener("touchstart", function(e) {

}, false);

canvas.addEventListener("touchmove", function(e) {
var touch = e.touches[0];
var me = new MouseEvent("mousemove", {
  clientX: touch.clientX,
  clientY: touch.clientY
});
canvas.dispatchEvent(me);
}, false);

canvas.addEventListener("touchstart", function(e) {
mousePos = getTouchPos(canvas, e);
var touch = e.touches[0];
var me = new MouseEvent("mousedown", {
  clientX: touch.clientX,
  clientY: touch.clientY
});
canvas.dispatchEvent(me);
}, false);

canvas.addEventListener("touchend", function(e) {
var me = new MouseEvent("mouseup", {});
canvas.dispatchEvent(me);
}, false);

function getMousePos(canvasDom, mouseEvent) {
var rect = canvasDom.getBoundingClientRect();
return {
  x: mouseEvent.clientX - rect.left,
  y: mouseEvent.clientY - rect.top
}
}

function getTouchPos(canvasDom, touchEvent) {
var rect = canvasDom.getBoundingClientRect();
return {
  x: touchEvent.touches[0].clientX - rect.left,
  y: touchEvent.touches[0].clientY - rect.top
}
}

function renderCanvas() {
if (drawing) {
  ctx.moveTo(lastPos.x, lastPos.y);
  ctx.lineTo(mousePos.x, mousePos.y);
  ctx.stroke();
  lastPos = mousePos;
}
}

// Prevent scrolling when touching the canvas
document.body.addEventListener("touchstart", function(e) {
if (e.target == canvas) {
  e.preventDefault();
}
}, false);
document.body.addEventListener("touchend", function(e) {
if (e.target == canvas) {
  e.preventDefault();
}
}, false);
document.body.addEventListener("touchmove", function(e) {
if (e.target == canvas) {
  e.preventDefault();
}
}, false);

(function drawLoop() {
requestAnimFrame(drawLoop);
renderCanvas();
})();

function clearCanvas() {
canvas.width = canvas.width;
}

// Set up the UI
var igText = document.getElementById("ig-dataUrl");
var igImage = document.getElementById("ig-image");
var clearBtn = document.getElementById("ig-clearBtn");
var submitBtn = document.getElementById("ig-submitBtn");
clearBtn.addEventListener("click", function(e) {
clearCanvas();
igText.innerHTML = "Data URL for your signature will go here!";
igImage.setAttribute("src", "");
}, false);
submitBtn.addEventListener("click", function(e) {
var dataUrl = canvas.toDataURL();
igText.innerHTML = dataUrl;
igImage.setAttribute("src", dataUrl);
}, false);

})();
  }
}
</script>


<style lang="scss" scoped>
$muted: #888;
$light-grey: #eee;
$muted: #888;
$light-grey: #eee;
$blue: #016BA8;
section{
  color: $muted;
  margin-top: 25px;

  h6{
    font-size: 18px;
  }
  h5{
    font-size: 24px;
  }
  .sub-heading{
    padding: 7.5px 0px;
  }
  .fa-check-circle{
    color: #4AC948;
  }
  input{
    border: none;
    border-bottom: 1px solid $light-grey;
    padding: 5px 0px;
    color: $muted;
    background: none;
    &:focus{
      border: none;
      outline: none;
    }
  }
  .top-list{
  li{
    padding: 5px 0px;
    list-style: none;
  }
}
}

.cardMain{
background: #fff;
margin: 20px 0px;
padding: 1rem;
border-radius: 10px;
box-shadow: 0px 0px 5px 3px rgba(0,0,0,0.1);
ul{
  list-style: none;
}
input{
  width: 80%;
  margin: 15px 0px;
}
}


#ig-canvas, #sig-canvas{
  background: #FAFAFA;
  border-radius: 15px;
  cursor: crosshair;
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.2);
  touch-action: none;
}

#ig-dataUrl, #sig-dataUrl{
  display: none;
}
.buttonMain{
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

</style>
