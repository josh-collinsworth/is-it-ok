<script lang="ts">
import Intro from './components/Intro.svelte'
import StepOne from './components/steps/StepOne.svelte'
import StepTwo from './components/steps/StepTwo.svelte'
import StepThree from './components/steps/StepThree.svelte'
import StepFour from './components/steps/StepFour.svelte'
import StepFive from './components/steps/StepFive.svelte'

import NotBothAdultsEnding from './components/endings/NotBothAdultsEnding.svelte'
import DidNotAskEnding from './components/endings/DidNotAskEnding.svelte'
import AreNotEqualsEnding from './components/endings/AreNotEqualsEnding.svelte'

import TransitionContainer from './components/TransitionContainer.svelte'

let step: number = 0
let bothAreOfAge: number
let hasRequested: number
let hasReallyRequested: number
let hasNoOtherMotives: number
let absolutelySure: number

$: endAfterStepOne = bothAreOfAge === 0 && step > 1
$: endAfterStepTwo = hasRequested === 0 && step > 2
$: endAfterStepThree = hasReallyRequested === 0 && step > 3
$: endAfterStepFour = hasNoOtherMotives === 1 && step > 4
$: endAfterStepFive = absolutelySure === 0 && step > 5

const goToStep = (nextStep: number): void => {
	step = nextStep
}

const resetForm = (): void => {
	step = 0
	bothAreOfAge = undefined
	hasRequested = undefined
	hasReallyRequested = undefined
	hasNoOtherMotives = undefined
	absolutelySure = undefined
}
</script>

<main>
	{#if step === 0}
		<Intro {goToStep} />
	{:else if step === 1}
		<StepOne bind:bothAreOfAge {goToStep} {step} />
	{:else if endAfterStepOne}
		<NotBothAdultsEnding {resetForm} />
	{:else if step === 2}
		<StepTwo bind:hasRequested {goToStep} {step} />
	{:else if endAfterStepTwo}
		<DidNotAskEnding {resetForm} />
	{:else if step === 3}
		<StepThree bind:hasReallyRequested {goToStep} {step} />
	{:else if endAfterStepThree}
		<DidNotAskEnding {resetForm} />
	{:else if step === 4}
		<StepFour bind:hasNoOtherMotives {goToStep} {step} />
	{:else if endAfterStepFour || endAfterStepFive}
		<AreNotEqualsEnding {resetForm} />
	{:else if step === 5}
		<StepFive bind:absolutelySure {goToStep} {step} />
	{:else}
		<TransitionContainer>
			{#if hasRequested}
				<h2><span>👍🏼</span> You're good.</h2>

				<p>While we're not necessarily saying you <em>should</em> send that dick pic, it sounds like you're both willing and consenting adults without any ulterior motives or misplaced expectations, so…good for both of you, we guess.</p>
			{:else}
				<h2><span>🛑</span> NOPE.</h2>

				<p>Do <strong>NOT</strong>, under <strong>any</strong> circumstances, send that dick pic.</p>
				<p>Somebody will thank us. (It might be you.)</p>

			{/if}
			<button on:click={resetForm}>Take again</button>
		</TransitionContainer>
	{/if}
</main>
