<script lang="ts">
  let flag=false;
  let name1;
  let name2;
  let valu=10;
  const refresh=()=>{
    if(flag==false){
      flag=true;
    }
    else{
      flag=false;
    }
  };
  const finall=()=>{
    if (flag==false){
      name2=name1*valu;
    }
    else{
      name1=name2*valu;
    }
  };
</script>
<div class="inp">
  <div class="inp__1">
    <input type="text" name="message" class="inpt__1"  bind:value={name1}/>
  </div>
  <div class="inp__but">
    <button class="fin" id="final" on:click={finall}>конвертировать</button>
    <button class="refre"id="refresh" on:click={refresh}><img src="src\папка\image-3.png" alt=""></button>
  </div>
  <div class="inp__1">
    <input type="text" class="inpt__1" id="input2" bind:value={name2}>
  </div>
</div>
<style>
  .inp{
    display: flex;
    justify-content: space-between;
    gap:30px;
  }
  .inp__but{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 30px;
  }
</style>