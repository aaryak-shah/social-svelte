<script>
  export let showLogs = false
  export let redirectUrl = null
  window._g_config = {
    showLogs,
    redirectUrl,
  }
</script>

<svelte:head>
  <script>
    window._g_SignOut = () => {
      try {
        var auth2 = gapi.auth2.getAuthInstance()
        auth2.signOut().then(function () {
          if (window._g_config.showLogs) {
            console.log('User signed out.')
          }
          if (window._g_config.redirectUrl !== null) {
            window.location.href = window._g_config.redirectUrl
          }
        })
      } catch (e) {
        console.error(e)
      }
    }
  </script>
  <script src="https://apis.google.com/js/platform.js" async defer></script>
</svelte:head>

<main>
  <div class="g-signin2" data-onsuccess="onSignIn" />
  <slot />
</main>

<style>
  .g-signin2 {
    display: none;
  }
</style>
