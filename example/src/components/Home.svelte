<script>
  import { navigate } from 'svelte-navigator'
  import { GoogleAuthData } from '../../include/index'
  let gAuthData
  let gBasicProfile

  const showData = () => {
    if (window._g_authResponse)
      gAuthData = JSON.stringify(window._g_authResponse)
    else gAuthData = 'No Auth Data'
    if (window._g_basicProfile)
      gBasicProfile = JSON.stringify(window._g_basicProfile)
    else gBasicProfile = 'No Profile Data'
    console.log(gAuthData)
    console.log(gBasicProfile)
  }
</script>

<main>
  <GoogleAuthData showLogs={false} />
  <h1>Hello Social!</h1>
  <p>Example app for the social-svelte package</p>
  <button class="login" on:click={() => navigate('/login')}>Login Page</button>
  <button class="logout" on:click={() => navigate('/logout')}
    >Logout Page</button
  >
  <button class="Show Data" on:click={() => showData()}>Show Data</button>
  {#if gAuthData}
    <p>{gAuthData}</p>
  {/if}
  {#if gBasicProfile}
    <p>{gBasicProfile}</p>
  {/if}
</main>
