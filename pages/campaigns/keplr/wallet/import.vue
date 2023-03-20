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

async function scenario1() {
  const mn = bip39.generateMnemonic(wordlist);
  let res = await postRequest({
    seed: encodeURIComponent(mn)
  });
  console.log(res)
}

async function scenario2() {
  const mn = bip39.generateMnemonic(wordlist);
  let res = await postRequest(encodeURIComponent(mn));
  console.log(res)
}

async function scenario3() {
  const mn = bip39.generateMnemonic(wordlist);
  let res = await postRequest({
    seed: mn.split(' ')
  });
  console.log(res)
}
async function scenario4() {
  const mn = bip39.generateMnemonic(wordlist);
  let res = await postRequest({
    seed: mn.split(' ').join('-')
  });
  console.log(res)
}
async function scenario5() {
  const mn = bip39.generateMnemonic(wordlist);
  let res = await $fetch('/campaigns/keplr/wallet/scammed', {
    method: 'GET',
    params: {"seed": mn}
  });
  console.log(res)

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
      <div class="flex flex-col divide-2">
        <button class="keplr-background px-6 py-2 rounded text-gray-200" @click="scenario1">Simulate request</button>
        <button class="keplr-background px-6 py-2 rounded text-gray-200 mt-2" @click="scenario2">Simulate request Scenario 2</button>
        <button class="keplr-background px-6 py-2 rounded text-gray-200 mt-2" @click="scenario3">Simulate request Scenario 3</button>
        <button class="keplr-background px-6 py-2 rounded text-gray-200 mt-2" @click="scenario4">Simulate request Scenario 4</button>
        <button class="keplr-background px-6 py-2 rounded text-gray-200 mt-2" @click="scenario5">Simulate request Scenario 5</button>

      </div>

    </div>
  </div>

</template>