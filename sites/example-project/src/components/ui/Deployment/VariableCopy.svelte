<script>
    import {blur} from 'svelte/transition'
    export let text = undefined;
    export let hideText = false
    let copied = false 

    const toggleCopied = function() {
        copied = false
    }

    export let copy = async (text) => {
      try {
        if(!copied) {
          await navigator.clipboard.writeText(text);
          copied = true
          setTimeout(toggleCopied, 2000)
        }
      } catch (e) {
      }
    };
  
    import Copy from "./CopyIcon.svelte";
  

  </script>

  <div 
    class=container 
    class:copied
    on:click="{() => {
      if (text !== undefined) {
          copy(text);
      };
    }}"
    >
    <span class=var-value>
    {#if copied}
    <span in:blur>Copied</span>
    {:else}
    <span in:blur>

      {@html hideText ? '&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;&middot;' : text}

    </span>
    {/if}

  </span>
  {#if copied}
  <Copy class="bx--snippet__icon" color='var(--green-900)'/>
  {:else}
  <Copy class="bx--snippet__icon"/>
  {/if}

</div>

  <style>
    div.container {
        box-sizing: border-box;
        background-color: var(--grey-100);
        border-radius: 4px 4px 4px 4px;
        border: 1px solid var(--grey-200);
        padding: 0.25em 0.25em 0.25em 0.25em;
        color: var(--grey-800);
        size: 0.75em;
        cursor: pointer;
        user-select: none;
        -webkit-user-select: none;
        -moz-user-select: none;
        display:flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        transition: all 400ms;
        width: 100%;
        font-family: var(--monospace-font-family);
    }

    div.container:hover {
        border-color: var(--blue-500);
        background-color: var(--blue-100);
        color: var(--blue-800);
        transition: all 400ms;
    }
    
    div.container:active {
        border-color: var(--green-500);
        background-color: var(--green-100);
        color: var(--green-800);
    }

    div.container.copied {
        border-color: var(--green-500);
        background-color: var(--green-100);
        color: var(--green-900);

    }

    span.var-value {
        width: 85%;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
     }


  </style>