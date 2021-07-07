<script>
  export let showLogs = false
  export let redirectUrl = null

  window._fb_config = {
    showLogs,
    redirectUrl,
  }
</script>

<svelte:head>
  <script
    async
    defer
    crossorigin="anonymous"
    src="https://connect.facebook.net/en_US/sdk.js"></script>
  <script>
    window.fbAsyncInit = () => {
      FB.init({
        appId: `${document
          .getElementsByName('facebook-signin-client_id')[0]
          .getAttribute('content')}`,
        cookie: true,
        xfbml: true,
        version: 'v11.0',
      })
    }
    window._fb_SignOut = () => {
      FB.logout((response) => {
        if (window._fb_config.showLogs) {
          console.log('Logged Out', response)
        }
        if (window._fb_config.redirectUrl !== null) {
          window.location.href = window._fb_config.redirectUrl
        }
      })
    }
  </script>
</svelte:head>

<main>
  <slot />
</main>
