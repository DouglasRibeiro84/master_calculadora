<script>
import { reactive } from 'vue';

export default {
    data() {
        return {
            evento: false,
            numeroAtual: "",
            primeiroNumero: null,
            operacao: null,
            resultado: null,
        };
    },

    methods: {
        alterarEstilo() {
            this.evento = !this.evento;
        },

        adicionarNumero(numero) {
            if (this.resultado !== null) {
                this.resultado = null;
                this.numeroAtual = numero.toString();
            } else {
                if (numero === ',' && !this.numeroAtual.includes(',')) {
                    this.numeroAtual += '.';
                } else if (numero !== ',') {
                    this.numeroAtual += numero.toString();
                }
            }
        },
        iniciarCalculo(operacao) {
            if (this.numeroAtual !== "") {
                this.primeiroNumero = parseFloat(this.numeroAtual);
                this.operacao = operacao;
                this.numeroAtual = "";
            }
        },
        calcular() {
            if (this.operacao && this.primeiroNumero !== null && this.numeroAtual !== "") {
                const segundoNumero = parseFloat(this.numeroAtual);
                let resultado;

                switch (this.operacao) {
                    case "+":
                        resultado = this.primeiroNumero + segundoNumero;
                        break;
                    case "-":
                        resultado = this.primeiroNumero - segundoNumero;
                        break;
                    case "*":
                        resultado = this.primeiroNumero * segundoNumero
                        break;
                    case "/":
                        resultado = this.primeiroNumero / segundoNumero
                        break;
                    case "%":
                        resultado = this.primeiroNumero % segundoNumero
                        break;
                    default:
                        resultado = 0;
                }
                this.resultado = resultado;
                this.numeroAtual = resultado.toString();
                this.operacao = null;
            }
        },

        limpar() {
            this.numeroAtual = "";
            this.primeiroNumero = null;
            this.operacao = null;
            this.resultado = null;
        },

        inverterSinal() {
            if (this.numeroAtual !== "") {
                this.numeroAtual = (parseFloat(this.numeroAtual) * -1).toString();
            } else if (this.resultado !== null) {
                this.resultado = this.resultado * -1
            }
        },
        removerUltimoCaractere() {
            if (this.numeroAtual !== "") {
                this.numeroAtual = this.numeroAtual.slice(0, -1);
    
                if (this.numeroAtual === ",") {
                    this.numeroAtual = "";
                }
            } else if (this.resultado !== null) {
                this.resultado = this.resultado.slice(0, -1);
            }
        }
    },


    computed: {
        visorValue() {
            if (this.resultado !== null) {
                return this.resultado;
            } else if (this.primeiroNumero !== null && this.operacao !== null) {
                return `${this.primeiroNumero} ${this.operacao} ${this.numeroAtual}`;
            } else {
                return this.numeroAtual
            }
        }
    }
}

</script>

<template>
    <div class="container" :class="{ dark: evento }">
        <div class="form-check form-switch">
            <h1 class="p-5 text-center">Escola o tipo de calculadora:<select class="p-3 rounded ms-4">
                    <option value="">normal</option>
                    <option value="">Regra de 3</option>
                </select>
                <input @change="alterarEstilo()" class="form-check-input float-end" type="checkbox">
            </h1>
        </div>
        <div class="corpo mt-5 p-5">
            <div class="row">
                <div class="col-md-4 col-sm-0"></div>
                <div class="col-md-4 col-sm-12">
                    <div class="card">
                        <div class="card-body p-4">
                            <div class="row p-2">
                                <input :value="visorValue" class="w-100 p-2 text-end visor" type="text" readonly />
                            </div>
                            <div class="row mt-3 d-flex justify-content-center pb-2">
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="limpar()" class="btn btn-danger ps-4 pe-4">ac</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="iniciarCalculo('%')" class="btn btn-dark ps-4 pe-4">%</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="iniciarCalculo('/')" class="btn btn-dark ps-4 pe-4">/</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="removerUltimoCaractere" class="btn btn-dark ps-4 pe-4"><i
                                            class="bi bi-backspace"></i></button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(7)" class="btn btn-numbers ps-4 pe-4">7</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(8)" class="btn btn-numbers ps-4 pe-4">8</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(9)" class="btn btn-numbers ps-4 pe-4">9</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="iniciarCalculo('*')" class="btn btn-dark ps-4 pe-4">x</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(4)" class="btn btn-numbers ps-4 pe-4">4</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(5)" class="btn btn-numbers ps-4 pe-4">5</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(6)" class="btn btn-numbers ps-4 pe-4">6</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="iniciarCalculo('-')" class="btn btn-dark ps-4 pe-4">-</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(1)" class="btn btn-numbers ps-4 pe-4"> 1 </button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(2)" class="btn btn-numbers ps-4 pe-4">2</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(3)" class="btn btn-numbers ps-4 pe-4">3</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="iniciarCalculo('+')" class="btn btn-dark ps-4 pe-4">+</button>
                                </div>
                            </div>
                            <div class="row mt-3 d-flex justify-content-center">
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="inverterSinal" class="btn btn-dark ps-3 pe-3">+/-</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(0)" class="btn btn-numbers ps-4 pe-4">0</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="adicionarNumero(',')" class="btn btn-dark ps-4 pe-4">,</button>
                                </div>
                                <div class="col-3 d-flex justify-content-center">
                                    <button @click="calcular" class="btn btn-success ps-4 pe-4">=</button>
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
    background-image: url(./images/background_img.png);
    background-size: cover;
    background-repeat: no-repeat;
    height: 100vh;
    max-width: 100%;
    transition: .8s ease-in-out;
}

.container.dark {
    background-image: url(./images/background_dark.png);
    transition: .8s ease-in-out;
}

.container.dark h1 {
    color: white;
    text-shadow: 4px 4px 0px black;
}

select {
    text-align: center;
    background-color: rgba(8, 8, 8, 0.712);
    color: white;
    outline: none;
    border: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    box-shadow: 0 0 0 .10rem rgba(255, 255, 255, 0.397);
}

h1 {
    font-family: "Rubik Glitch", system-ui;
    font-weight: 400;
    font-style: normal;
    color: #20083A;
    text-shadow: 4px 4px 0px white;
    font-size: 40px;
    line-height: 50px;
}

.visor {
    outline: none;
    border: none;
    background-color: #043513cc;
    border-radius: 10px;
    border: 1px solid #24f04971;
    font-family: "Rubik Gemstones", system-ui;
    color: #4DE35E;
    font-size: 30px;
}

.visor::-webkit-outer-spin-button,
.visor::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

.form-check-input {
    --bs-form-check-bg: #f9f9f9c4
}

.form-check-input:focus {
    border-color: transparent;
    box-shadow: 0 0 0 .10rem rgba(255, 255, 255, 0.233)
}

.form-check-input:checked {
    border: transparent;
    background-color: rgba(255, 255, 255, 0.11);
    box-shadow: 0 0 0 .10rem rgba(255, 255, 255, 0.233)
}

@keyframes changeBoxShadowColorDark {
    0% {
        box-shadow: 0 0px 10px .15rem rgba(248, 248, 248, 0.5);
    }

    33% {
        box-shadow: 0 0px 10px .15rem rgb(81, 72, 87);
    }

    66% {
        box-shadow: 0 0px 10px .15rem rgba(53, 53, 88, 0.993);
    }

    100% {
        box-shadow: 0 0px 10px .15rem rgba(255, 255, 255, 0.63);
    }
}

.container.dark .card {
    animation: changeBoxShadowColorDark 4s cubic-bezier(0.25, 0.8, 0.25, 1) infinite;
}

@keyframes changeBoxShadowColor {
    0% {
        box-shadow: 0 0px 10px .15rem rgba(248, 248, 248, 0.5);
    }

    33% {
        box-shadow: 0 0px 10px .15rem rgb(40, 54, 241);
    }

    66% {
        box-shadow: 0 0px 10px .15rem rgb(1, 223, 252);
    }

    100% {
        box-shadow: 0 0px 10px .15rem rgba(255, 255, 255, 0.63);
    }
}

.card {
    animation: changeBoxShadowColor 4s cubic-bezier(0.25, 0.8, 0.25, 1) infinite;
}

.card {
    background-color: #20083ab9;
}

.container.dark .card {
    background-color: #131214b7;
}

.btn,
.btn:hover {
    border: 1px solid rgba(255, 255, 255, 0.664);
    font-family: "Rowdies", sans-serif;
    font-size: 18px;
}

.btn.btn-numbers {
    background-color: #CE5DD9;
    color: white;
    font-family: "Rowdies", sans-serif;
    font-size: 24px;
    width: 100%;
}

.container.dark .btn.btn-numbers {
    background-color: #0B0B0B
}
</style>