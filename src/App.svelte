<script lang="ts">
import NotBothAdultsEnding from './components/endings/NotBothAdultsEnding.svelte'
import DidNotAskEnding from './components/endings/DidNotAskEnding.svelte'
import StepOne from './components/steps/StepOne.svelte'
import StepThree from './components/steps/StepThree.svelte';
import StepTwo from './components/steps/StepTwo.svelte'
import TransitionContainer from './components/TransitionContainer.svelte'

let step: number = 0
let bothAreOfAge: boolean
let hasRequested: boolean
let hasReallyRequested: boolean
$: endAfterStepOne = bothAreOfAge !== true && step > 1
$: endAfterStepTwoOrThree = (hasRequested !== true || hasRequested !== true) && step > 2

const goToStep = (nextStep: number): void => {
	step = nextStep
}

const resetForm = (): void => {
	step = 0
	hasRequested = undefined
}
</script>

<main>
{bothAreOfAge}, {step}

	{#if step === 0}
		<TransitionContainer>
			<h1>
				<span aria-hidden="true">🍆 📸</span>
				Should I send a&nbsp;dick&nbsp;pic?
			</h1>

			<p>Considering sending a dick pic, but not sure whether it's ok?</p>

			<p><b>You’re in the right place!</b></p>

			<div>
				<button on:click={() => goToStep(1)} disabled={step !== 0}>
					Click here to take the survey
				</button>
			</div>
		</TransitionContainer>
	{/if}

	{#if step === 1}
		<StepOne bind:bothAreOfAge {goToStep} />
	{:else if endAfterStepOne}
		<NotBothAdultsEnding {resetForm} />
	{:else if step === 2}
		<StepTwo bind:hasRequested {goToStep} />
	{:else if endAfterStepTwoOrThree}
		<DidNotAskEnding {resetForm} />
	{:else if step === 3}
		<StepThree bind:hasReallyRequested {goToStep} />
	{:else}
		<TransitionContainer>
			{#if hasRequested}
				<h2><span>👍🏼</span> You're good.</h2>

				<p>While we're not necessarily saying you <em>should</em> send that dick pic, it sounds like you're both willing and consenting adults, so…good for both of you, we guess.</p>
			{:else}
				<h2><span>🛑</span> NOPE.</h2>

				<p>Do <strong>NOT</strong>, under <strong>any</strong> circumstances, send that dick pic.</p>
				<p>Somebody will thank us. (It might be you.)</p>

				{/if}
				<button on:click={resetForm}>Take again</button>
		</TransitionContainer>
	{/if}
</main>
