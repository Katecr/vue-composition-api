<template>
  <div>
    <button @click="toggle">Modal</button>
    
    <teleport to="body">
        <div v-show="show" class="modal">

            <!-- Modal content -->
            <div class="modal-content">
                <p>Some text in the Modal..</p>
                <button @click="toggle" class="close">Cerrar</button>
            </div>

        </div>
    </teleport>
  </div>
</template>

<script>
    export default {
    data() {
        return {
        show: false,
        };
    },
    methods: {
        toggle() {
        this.show = !this.show;
        },
    },
    };
</script>

<style>


/* The Modal (background) */
.modal {
   /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
}

/* Modal Content */
.modal-content {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.modal-content p{
    color:#000;
}
/* The Close Button */
.close {
  color: #aaaaaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
</style>