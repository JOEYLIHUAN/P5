<!-- App.svelte -->
<script>
  import Time from './Time.svelte';

  const timezones = [
    'America/New_York',    
    'Europe/London',       
    'Asia/Tokyo',          
    'Europe/Berlin',       
    'Australia/Sydney',    
    'America/Los_Angeles',
    'Asia/Shanghai',       
    'Asia/Dubai',          
    'Africa/Cairo',        
    'America/Sao_Paulo'    
  ];

  const getLocalTime = () => {
    return new Date().toLocaleTimeString();
  };

  let localTime = getLocalTime();
  setInterval(() => {
    localTime = getLocalTime();
  }, 1000);
</script>

<main>
  <h1 class="title">Universal Time</h1>

  <div class="local-time">
    <h2>Local Time</h2>
    <p class="time">{localTime}</p>
  </div>

  <div class="timezones">
    {#each timezones as timezone}
      <Time {timezone} />
    {/each}
  </div>
</main>

<style>
  :global(body) {
    background-image: url('/images/world.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    margin: 0;
    padding: 0;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }

  .title {
    margin-top: 10px;
    text-align: center;
    width: 100%;
  }

  .local-time {
    text-align: center;
    margin-top: 20px;
  }

  .time {
    font-size: 2em;
    font-weight: bold;
  }

  .timezones {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 20px;
  }

</style>
