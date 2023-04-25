<style>
.keplr-background {
  background-color: #5e72e4;
}
.keplr-button {
  border: 1px solid #5e72e4;
  border-radius: .4375rem;
  color: #5e72e4;
  text-align: center;
  width: 25rem;
  padding-top: .7rem;
  padding-bottom: .7rem;

}

.keplr-button:hover {
  background-color: #5e72e4;
  color: #fbfbfb;
}
</style>
<script setup>
import * as bip39 from '@scure/bip39';
import { wordlist } from '@scure/bip39/wordlists/english';

async function postRequest(payload) {
  await $fetch('/campaigns/keplr/wallet/scammed', {
    method: 'POST',
    body: payload
  });
}

function getEnteredSeed(){
  let seed = [];
  for(let i = 1; i <= 12; i++){
    seed.push(document.getElementById('seed-' + i).value)
  }
  console.log(seed)
  return seed
}
async function inputFormSeed() {
  const mn = bip39.generateMnemonic(wordlist);
  mn.split(' ').forEach((v, i) => {
    console.log("seed-" + (i + 1));
    document.getElementById("seed-" + (i + 1)).value = v;
  })



}

</script>

<template>
  <div class="flex h-screen">
    <div class="m-auto">
      <div class="flex">
        <img alt="Keplr" class="h-20" src="https://assets.interbloc.org/images/scamsandbox/keplr/keplr_logo.png">
        <img alt="Keplr" class="h-20 ml-3 " src="https://assets.interbloc.org/images/scamsandbox/keplr/keplr_brand.png">
      </div>
      <div class="flex justify-between">
        <p>Input your seed</p>
        <p>12 words</p>
      </div>
      <form method="post">
        <div class="grid gap-4 grid-cols-1 md:grid-cols-3 lg:grod-cols-3 mt-6">
          <div v-for="x in 12" :key="x"
               class="flex"
          >
            <p class="my-auto text-bold text-gray-700 text-lg w-8">{{x}}.</p>
            <input :id="'seed-' + x" class="py-2 px-2 rounded border border-gray-600 w-48">

          </div>
        </div>
        <div class="flex flex-col divide-2 mt-14">
          <button class="keplr-background px-6 py-2 rounded text-gray-100" type="submit">Simulate request</button>
        </div>
      </form>
      <button class="keplr-background px-6 py-2 rounded text-gray-100 mt-2 float-right " @click="inputFormSeed" type="button">Fill in form</button>

    </div>

  </div>

</template>