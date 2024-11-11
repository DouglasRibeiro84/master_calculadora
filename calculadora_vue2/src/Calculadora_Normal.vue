<script>
export default {
    data() {
        return {
            evento: false,
        };
    },
    methods: {
        alterarEstilo(){
            
        }
    }
};

</script>

<template>
    <div class="container" :class="{ dark: evento }">
        <div class="form-check form-switch">
            <h1 class="p-5 text-center">Escola o tipo de calculadora <select>
                    <option value="">normal</option>
                    <option value="">Regra de 3</option>
                </select>
                <input v-model="evento" @change="alterarEstilo()" class="form-check-input float-end" type="checkbox">
            </h1>
        </div>
        <div class="corpo mt-5 p-5">
            <div class="row">
                <div class="col-4"></div>
                <div class="col-4">
                    <div class="card">
                        <div class="card-body p-4">
                            <div class="row p-2">
                                <input class="w-100 p-2 text-end" type="number" name="" id="">
                            </div>
                            <div class="row mt-3 d-flex justify-content-center pb-2">
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-danger ps-4 pe-4">ac</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4">%</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4">/</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4"><i class="bi bi-backspace"></i></button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">7</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">8</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">9</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4">x</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">4</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">5</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">6</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4">-</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">1</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">2</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">3</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-4 pe-4">+</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-dark ps-3 pe-3">+/-</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">0</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-primary ps-4 pe-4">,</button>
                                </div>
                                <div class="col-md-3 d-flex justify-content-center">
                                    <button class="btn btn-success ps-4 pe-4">=</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    background-color: rgb(184, 61, 153);
    height: 100vh;
}

.container.dark {
    background-color: rgba(0, 0, 0, 0.582);
    height: 100vh;
}
</style>