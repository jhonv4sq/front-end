<template>
  <div>
    <div class="spinner"></div>
  </div>
</template>

<style>
.spinner{
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: conic-gradient(
       #0000 10%,
       #4105f5
     );
    -webkit-mask:
       radial-gradient(
          farthest-side,
         #0000 calc(100% - 10px),
         #000
         0
        );
    animation:spin 0.8s infinite linear;
}
@keyframes spin{
    to{
    transform:rotate(1turn);
    }
}
</style>