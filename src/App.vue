<template>
  <div>
	<textarea id="" cols="30" rows="10" v-model="inputText"></textarea>
	<button @click="correctText"></button>
  </div>
</template>

<script lang="ts">

declare interface Data {
	dictionary: { [key: string]: boolean },
	textCorectat: string,
	inputText: string
};

import { textDictionar } from './assets/textDictionar';

export default {
	name: 'App',
	data(): Data {
		return {
			dictionary: {},
			textCorectat: '',
			inputText: ''
		};
	},
	setup() {
		return { textDictionar };
	},
	methods: {
		genereazaDictionar() {
			let cuvinte = this.textDictionar.split(/\s+/);

			for (let i = 0; i < cuvinte.length; i++) {
				let cuvant = cuvinte[i].toLowerCase().replace(/[^\w\șțâăî]|[\d]/gi, '');

				if (cuvant !== '') {
					this.dictionary[cuvant] = true;
				}
			}
		},
		corectareText() {
			this.inputText = this.inputText.replace(/\s+/g, " ");
			this.inputText = this.inputText.replace(/([,.])(?!\s)/g, "$1 ");
			this.inputText = this.inputText.replace(/\s+([,.])/g, "$1");

			if (this.inputText.length > 0) {
				if (this.inputText.charAt(0) === " ") {
					this.inputText = this.inputText.slice(1);
				}
				if (this.inputText.charAt(this.inputText.length - 1) === " ") {
					this.inputText = this.inputText.slice(0, -1);
				}
  			}

			let cuvinte = this.inputText.split(" ");
			let textCorectat = "";

			for (let i = 0; i < cuvinte.length; i++) {
				let cuvant = cuvinte[i].toLowerCase().replace(/[^\w\șțâăî:()]|[\d]/gi, '');

				if (this.dictionary[cuvant]) {
					textCorectat += cuvinte[i];
				} else {
					let cuvantCorectat = this.corecteazaCuvant(cuvant);
					textCorectat += cuvantCorectat;
				}

				if (i < cuvinte.length - 1) {
					textCorectat += " ";
				}
			}

			this.textCorectat = textCorectat.trim();
		},
		corecteazaCuvant(cuvant: string) {
			const ngramSize = 2;
			const cuvinteDictionar = Object.keys(this.dictionary);
			const cuvanteNgram = this.generareNgram(cuvant, ngramSize);

			let celMaiPotrivitCuvant = cuvant;
			let celMaiMicDistanta = Infinity;

			for (let i = 0; i < cuvinteDictionar.length; i++) {
				const cuvantDictionar = cuvinteDictionar[i];
				const cuvinteDictionarNgram = this.generareNgram(cuvantDictionar, ngramSize);
				const distanta = this.calculDistantaNgram(cuvanteNgram, cuvinteDictionarNgram);

				if (distanta < celMaiMicDistanta) {
					celMaiMicDistanta = distanta;
					celMaiPotrivitCuvant = cuvantDictionar;
				}
			}

			return celMaiPotrivitCuvant;
		},
		generareNgram(cuvant: string, n: number) {
			const cuvinteNgram = [];

			for (let i = 0; i < cuvant.length - n + 1; i++) {
				const ngram = cuvant.slice(i, i + n);
				cuvinteNgram.push(ngram);
			}

			return cuvinteNgram;
		},
		calculDistantaNgram(ngram1: any, ngram2: any) {
			const setNgram1 = new Set(ngram1);
			const setNgram2 = new Set(ngram2);
			const intersectie = [...setNgram1].filter(ngram => setNgram2.has(ngram));

			return ngram1.length + ngram2.length - 2 * intersectie.length;
		},
		correctText() {
			this.corectareText();
			console.log(this.textCorectat);
		}
	},
	mounted() {
		this.genereazaDictionar();


		console.log(this.dictionary);
	}
};
</script>
