<script>
    import EnvironmentVarListing from "./EnvironmentVarListing.svelte";
    import VariableCopy from "./VariableCopy.svelte";
    export let settings
</script>

{#if !settings.credentials}
<p>You'll need to connect to a database before deploying to Vercel.</p>
{:else if !settings.gitRepo}
<p>You'll need to set up a git repo before deploying to Vercel.</p>
{:else }

<h1>Deploying to Vercel</h1>

<ol>
    <li><a href='https://vercel.com/new' target=_blank>Start a new Vercel project &rarr;</a></li>
    <li>Choose the repo containing this project</li>
    <li>Configure your project to match the settings below</li>

</ol>

<div class="separator">Build and Output Settings</div>

<div class='setting-row'>
    <span class='setting'>Build Command</span>
    <div class='setting-value'><VariableCopy text={'npm run build'}/></div>
</div>


<div class='setting-row'>
    <span class='setting'>Output Directory</span>  
    <div class='setting-value'><VariableCopy text={'build/'}/> </div>
</div>

<div class='setting-row'>
    <span class='setting'>Install Command</span>  
    <div class='setting-value'><VariableCopy text={'build/'}/> </div>
</div>


<div class="separator">Environment Variables</div>
<p>Copy paste the following into environment variables</p>

<EnvironmentVarListing {settings}/>

<h2>Optional </h2>
<ol>
    <li><a href='https://vercel.com/blog/protecting-deployments'>Password protect your site</a></li>
    <li> <a href='https://docs.evidence.dev/deployment/vercel#optional-schedule-updates-using-deploy-hooks'>Schedule your site to update periodically</a></li>
</ol>

{/if}

<style>
    a {
        color: var(--blue-600);
        text-decoration: none;
    }

    a:hover {
        color: var(--blue-800);
        text-decoration: none;
    }

    span.setting {
        font-size: 0.85em;
        color: var(--grey-800);
        text-transform: uppercase;
        letter-spacing: 0.05em;
    }

    div.setting-row {
        margin-top: 1.25em;
    }

    div.setting-row:first-of-type {
        margin-top: 0em;
    }

    div.setting-value {
        margin-top: 0.25em;
        width: 45%;
    }

    .separator {
        display: flex;
        align-items: center;
        text-align: center;
        margin-block-start: 2.5em;
        color: var(--grey-700);
        font-weight:bold;
    }

    .separator::after {
        content: '';
        flex: 1;
        border-bottom: 1px solid var(--grey-200);
    }

    .separator:not(:empty)::after {
        margin-left: 1.5em;
        margin-top: 0.1em;
    }

</style>