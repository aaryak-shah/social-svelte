<script>
  import { Router, Route, Link, navigate } from 'svelte-navigator'
  import Home from './components/Home.svelte'
  import Login from './components/Login.svelte'
  import Logout from './components/Logout.svelte'
</script>

<main>
  <Router primary={false}>
    <Route path="/" component={Home} />
    <Route path="/login" component={Login} />
    <Route path="/logout" component={Logout} />
  </Router>
</main>
