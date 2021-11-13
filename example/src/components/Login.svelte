<script>
  import { GoogleSignIn } from '../../include/index'
</script>

<main>
  <h1>Login</h1>
  <GoogleSignIn redirectUrl="/" showLogs={false}>
    <div on:click={window['_g_SignIn']} class="gsignin-btn">
      Log in with Google
    </div>
  </GoogleSignIn>
</main>

<style>
  .gsignin-btn {
    border: 2px solid black;
    border-radius: 10px;
    font-weight: bold;
    text-align: center;
    width: 200px;
    padding: 10px 20px;
  }
  .gsignin-btn:hover {
    cursor: pointer;
    background: linear-gradient(to right, orange, orangered);
  }
</style>
