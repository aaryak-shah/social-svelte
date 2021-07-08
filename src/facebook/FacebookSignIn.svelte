<script>
  export let showLogs = false
  window._fb_config = {
    showLogs,
  }
</script>

<svelte:head>
  <script
    async
    defer
    crossorigin="anonymous"
    src="https://connect.facebook.net/en_US/sdk.js"></script>
  <script>
    window.statusChangeCallback = (response) => {
      if (window._fb_config.showLogs) {
        console.log(response)
      }
      if (response.status == 'connected') {
        checkLoginState()
        getUserData()
      }
    }
    window.fbAsyncInit = () => {
      FB.init({
        appId: `${document
          .getElementsByName('facebook-signin-client_id')[0]
          .getAttribute('content')}`,
        cookie: true,
        xfbml: true,
        version: 'v11.0',
      })

      FB.getLoginStatus((response) => {
        statusChangeCallback(response)
      })
    }
    window._fb_SignIn = () => {
      try {
        FB.login(statusChangeCallback, {
          scope: 'public_profile,email',
          return_scopes: true,
        })
      } catch (error) {
        console.error(error)
      }
    }
    window.checkLoginState = () => {
      FB.getLoginStatus((response) => {
        // Allows access to login status from window._fb_loginStatus
        window._fb_loginStatus = response
      })
    }
    window.getUserData = () => {
      FB.api('/me', (meResponse) => {
        // Allows access to "me" from window._fb_me
        window._fb_me = meResponse
        if (window._fb_config.showLogs) {
          console.log('me', meResponse)
        }
        FB.api(
          `/${meResponse.id}`,
          'GET',
          {
            fields:
              'id,about,age_range,first_name,last_name,email,picture.type(large)',
          },
          (userResponse) => {
            // Allows access to user data from window._fb_user
            window._fb_user = userResponse
            if (window._fb_config.showLogs) {
              console.log('user', userResponse)
            }
          }
        )
      })
    }
  </script>
</svelte:head>

<main>
  <slot />
</main>
