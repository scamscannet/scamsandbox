<style>
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

<template>
  <div class="flex h-screen">
    <div class="m-auto">
      <div class="flex justify-center">
        <img alt="Keplr" class="h-20" src="https://assets.interbloc.org/images/scamsandbox/keplr/keplr_logo.png">
        <img alt="Keplr" class="h-20 ml-3 " src="https://assets.interbloc.org/images/scamsandbox/keplr/keplr_brand.png">
      </div>
      <img alt="Keplr" class="h-3 mx-auto mt-2" src="https://assets.interbloc.org/images/scamsandbox/keplr/keplr_sub_text.png">
      <a href="#">
        <div class="keplr-button mt-8">
          <p>Sign in with Google</p>
        </div>
      </a>

      <p class="text-sm text-gray-200 text-center mt-2">powered by Torus</p>
      <div class="w-full border-b-2 border-gray-200 mt-4 mb-6"></div>
      <a href="#">
        <div class="keplr-button">
          <p>Create new Account</p>
        </div>
      </a>
      <a href="#">
        <div class="keplr-button mt-2">
          <p>Import existing Account</p>
        </div>
      </a>
      <p class="text-sm text-gray-300 text-center mt-8">All sensitive information is stored only on your device.<br>
        This process does not require an internet connection.</p>

    </div>
  </div>


</template>