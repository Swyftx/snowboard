<script>
  import qs from "querystringify";

  export let authOptions;
  export let fullWidth;

  $: authorizeParams = qs.stringify(
    {
      client_id: authOptions.clientId,
      redirect_uri: authOptions.callbackUrl,
      response_type: "code",
      scope: authOptions.scopes || ""
    },
    true
  );

  $: authorizeUrl = `${authOptions.authorizeUrl}${authorizeParams}`;
</script>

<a
  href={authorizeUrl}
  class="button is-dark is-rounded"
  class:is-fullwidth={fullWidth}>
  <span class="icon">
    <i class="fas fa-sign-in-alt" aria-hidden="true" />
  </span>
  <span>Login</span>
</a>
