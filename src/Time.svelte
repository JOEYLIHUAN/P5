<!-- Time.svelte -->
<script>
    export let timezone;
  
    const updateTime = () => {
      const now = new Date().toLocaleTimeString('en-US', { timeZone: timezone });
      return now;
    };
  
    let currentTime = updateTime();
  
    setInterval(() => {
      currentTime = updateTime();
    }, 1000);
</script>

<div class="time-container">
  <b>{timezone}</b>: {currentTime}
</div>

<style>
  .time-container {
    margin: 10px;
    font-size: 0.8em;
  }
</style>
