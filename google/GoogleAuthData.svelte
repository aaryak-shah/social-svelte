<script>
  export let showLogs = false
  window._g_config = {
    showLogs,
  }
</script>

<svelte:head>
  <script>
    window.onSignIn = (googleUser) => {
      window._g_basicProfile = googleUser.getBasicProfile()
      window._g_authResponse = googleUser.getAuthResponse()
      if (window._g_config.showLogs) {
        console.log('id_token', _g_authResponse.id_token)
        console.log('ID: ' + _g_basicProfile.getId()) // Do not send to your backend! Use an ID token instead.
        console.log('Name: ' + _g_basicProfile.getName())
        console.log('Image URL: ' + _g_basicProfile.getImageUrl())
        console.log('Email: ' + _g_basicProfile.getEmail()) // This is null if the 'email' scope is not present.
      }
    }
  </script>

  <script src="https://apis.google.com/js/platform.js" async defer></script>
</svelte:head>

<main>
  <div class="g-signin2" data-onsuccess="onSignIn" />
</main>

<style>
  .g-signin2 {
    display: none;
  }
</style>
