<script setup>
import { ref } from 'vue';
import translate from './translate.json';

const darkmode = ref(false);
const lang = ref('en');
</script>

<template>
	<v-container>
		<div class="text-center">Typography</div>

		{{ lang }}
		{{ translate[lang] }}

		<v-row>
			<v-col> title btn </v-col>
			<v-col>
				<v-switch
					label="Switch"
					color="secondary"
					v-model="darkmode"
				></v-switch>
				<v-btn variant="text">
					{{ translate[lang]['change-language'] }}
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

<style scoped></style>
