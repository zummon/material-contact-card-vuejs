<script setup>
import { ref, computed, watch } from 'vue';
import translate from './translate.json';

const darkmode = ref(false);
const lang = ref('en');

const translation = computed(() => translate[lang.value].translation);

watch(darkmode,() => {
	
})
</script>

<template>
	<v-container>
		<div class="text-center">{{ translation['translate-by'] }}</div>

		<v-row>
			<v-col>
				<p class="text-h4">{{ translation['headline'] }}</p>
				<v-btn
					variant="text"
					class=""
					href="https://zummon.page/"
					target="_blank"
				>
					{{ translation['sub-headline'] }}
				</v-btn>
			</v-col>
			<v-col>
				<v-switch
					:label="translation['toggle-dark-mode']"
					color="secondary"
					v-model="darkmode"
				></v-switch>
				<v-btn variant="text">
					{{ translation['change-language'] }}
					<v-menu activator="parent">
						<v-list>
							<v-list-item
								v-for="(lng, index) in translate"
								:key="`lang-${index}`"
								:value="lng"
							>
								<v-list-item-title>{{ translate[lng].name }}</v-list-item-title>
							</v-list-item>
						</v-list>
					</v-menu>
				</v-btn>
			</v-col>
		</v-row>
	</v-container>
</template>
