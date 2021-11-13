<script>
  import { GoogleSignOut } from '../../include/index'
</script>

<main>
  <h1>Logout</h1>
  <GoogleSignOut redirectUrl="/" showLogs={false}>
    <div on:click={window['_g_SignOut']} class="gsignin-btn">
      Log out of Google
    </div>
  </GoogleSignOut>
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
