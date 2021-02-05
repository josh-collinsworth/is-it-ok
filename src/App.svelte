<script lang="ts">
	let step: number = 0
</script>

<main>
	<h1>
		Should I send a&nbsp;dick&nbsp;pic?
		<br />
		<span aria-hidden="true">🍆 📸</span>
	</h1>

	<p>Considering sending a dick pic, but not sure whether you&nbsp;should?</p>

	<p><b>You’re in the right place!</b></p>

	{#if step === 0}
		<button on:click={() => step = 1}>
			Click here to take the survey!
		</button>
	{/if}

	{#if step > 0}
		<form on:submit|preventDefault >
			<fieldset>

				<legend><b>1.)</b> Has the recipient specifically, in no uncertain terms, requested a picture of <em>your</em> dick, <em>recently</em>, of their own free will, under no pressure of any kind, and with nothing whatsoever to gain from said transaction except, of course, a picture of your dick, which, again, they have explicitly stated that they want to receive?</legend>

				<div class="choices">
					<div>
						<input class="sr" type="radio" id="yes" name="has-requested-dick-pic">
						<label for="yes">Yes</label>
					</div>
					<div>
						<input class="sr" type="radio" id="no" name="has-requested-dick-pic">
						<label for="no">No</label>
					</div>
				</fieldset>
		</form>
	{/if}
</main>

<style>
	main {
		padding: 1rem;
		width: 100%;
		margin: 0 auto;
	}

	h1 {
		color: var(--darkBlue);
		font-weight: bold;
	}

	@media (min-width: 640px) {
		main {
			max-width: 38rem;
		}
	}

	form {
		text-align: left;
	}
</style>
