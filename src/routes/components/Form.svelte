<script>
  let email = '';
  let password = '';
  let confirmPass = '';
  let error = false;
  let register = false;

  function handleAuthenticate() {
    if (!email || !password || (register && !confirmPass)) {
      error = true;
      return;
    }
  }

  function handleRegister() {
    register = !register;
  }
</script>

<main class="flex flex-col items-center justify-center px-10 h-screen">
  <form class="flex flex-col gap-3 w-96 max-w-full">
    <h1 class="text-center text-4xl font-bold mb-5 text-slate-600">{register ? "Registrar" : "Login"}</h1>
    {#if error}
      <p class="text-center text-red-700">A informação inserida não está correta</p>
    {/if}
    
    <label class="w-full relative border-2 border-slate-400 rounded-lg">
      <p class={email ? 'above' : 'center'}>Email</p>
      <input
        bind:value={email}
        class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
        type="email"
        placeholder="Email"
      >
    </label>
    <label class="w-full relative border-2 border-slate-400 rounded-lg">
      <p class={password ? 'above' : 'center'}>Senha</p>
      <input
        bind:value={password}
        class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
        type="password"
        placeholder="Senha"
      >
    </label>
    {#if register}
      <label class="w-full relative border-2 border-slate-400 rounded-lg">
        <p class={confirmPass ? 'above' : 'center'}>Confirme sua senha</p>
        <input
          bind:value={confirmPass}
          class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
          type="password"
          placeholder="Confirme sua senha"
        >
      </label>
    {/if}

    <button class="py-3 border-none rounded-lg text-white bg-slate-600 ease-in-out duration-500 hover:bg-slate-400">Enviar</button>
  </form>
  <div class="flex flex-col gap-5 py-4 overflow-hidden w-96 max-w-96 my-5">
          <p class="text-center x-5 my-auto text-slate-500">Ou</p>
         <!-- <p class="relative text-center x-5 my-auto text-slate-500 after:content-[''] after:absolute after:top-1/2 after:mx-2 after:-translate-y-1/2 after:w-full after:h-[1.5px] before:bg-slate-500 before:content-[''] before:absolute before:top-1/2 before:mx-2 before:translate-y-1/2 before:w-full before:h-[1.5px] before:bg-slate-500">Ou</p> -->
     
    {#if register}
      <div class="flex gap-1 justify-center">
        <p>Já possui uma conta?</p>
        <button on:click={handleRegister} on:keydown={() => {}} class="text-blue-500 cursor-pointer underline">Entrar</button>
      </div>
    {:else}
      <div class="flex gap-1 justify-center">
        <p>Não possui conta?</p>
        <button on:click={handleRegister} on:keydown={() => {}} class="text-blue-500 cursor-pointer underline">Registrar</button>
      </div>
    {/if}
  </div>

</main>

<style>
  .above, .center {
    position: absolute;
    transform: translateY(-50%);
    padding: 0 0.5rem;
    pointer-events: none;
    border-radius: 4px;
    font-size: 0.8rem;

    transition: 0.4s ease-in-out;

    color: white;
  }

  .above {
    top: 0;
    left: 1rem;
    border: 1px solid #94a3b8;
    font-size: 0.75rem;

    background-color: #94a3b8;
  }

  .center {
    /* top: 100%; */
    left: 0;
    border: 1px solid transparent;
    opacity: 0;
  }
</style>