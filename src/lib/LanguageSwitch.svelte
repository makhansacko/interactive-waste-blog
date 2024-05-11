<script>
    import { createEventDispatcher } from 'svelte';
    import {Button} from 'carbon-components-svelte';

    const dispatch = createEventDispatcher();
    let selectedLanguage = 'fr';

    function switchLanguage() {
        selectedLanguage = selectedLanguage === 'fr' ? 'en' : 'fr';
        dispatch('languageChanged', selectedLanguage);
    }
</script>

<div class="language-switch">
<Button on:click={switchLanguage} kind="secondary">
    {selectedLanguage === 'fr' ? 'English' : 'Français'}
</Button>
</div>

<style>
    .language-switch {
    position: fixed;
    top: 0;
    right: 0;
  }
</style>

