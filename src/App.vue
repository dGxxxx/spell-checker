<template>
	<main>
		<div class="area-region">
			<textarea id="inputArea" v-model="inputText" spellcheck="false" @keyup="countWords"></textarea>
			<div class="bottom">
				<div class="left">
					Total Cuvinte - {{ totalWords }}
				</div>
				<div class="right">
					<svg width="23" height="23" viewBox="0 0 23 23" fill="none" xmlns="http://www.w3.org/2000/svg" @click="copyText()">
						<path d="M13.6562 4.3125H12.9375V7.90625H16.5312V7.1875H13.6562V4.3125Z" fill="black"/>
						<path d="M14.6131 2.875H7.1875V5.03125H5.03125V20.125H15.8125V17.9688H17.9688V6.24414L14.6131 2.875ZM15.0938 19.4062H5.75V5.75H7.1875V17.9688H15.0938V19.4062ZM17.25 17.25H7.90625V3.59375H14.3166L17.25 6.54063V17.25Z" fill="black"/>
					</svg>

					<svg width="19" height="19" viewBox="0 0 19 19" fill="none" xmlns="http://www.w3.org/2000/svg" @click="saveText()">
						<path d="M9.02929 15.1629C8.93479 15.1627 8.8414 15.1425 8.75518 15.1039C8.66897 15.0652 8.59186 15.0088 8.52886 14.9383L2.22542 7.94803C2.13881 7.85119 2.08203 7.73137 2.06194 7.60301C2.04185 7.47465 2.05929 7.34322 2.11217 7.22454C2.16506 7.10587 2.25112 7.00501 2.36 6.93412C2.46888 6.86323 2.59593 6.82533 2.72585 6.82498H5.25001V0.673828C5.25001 0.495118 5.321 0.323727 5.44737 0.19736C5.57374 0.0709924 5.74513 0 5.92384 0H12.1365C12.3152 0 12.4866 0.0709924 12.613 0.19736C12.7394 0.323727 12.8104 0.495118 12.8104 0.673828V6.82318H15.3332C15.4631 6.82353 15.5902 6.86143 15.699 6.93233C15.8079 7.00322 15.894 7.10407 15.9469 7.22275C15.9997 7.34142 16.0172 7.47286 15.9971 7.60122C15.977 7.72958 15.9202 7.84939 15.8336 7.94623L9.52972 14.9401C9.46656 15.0102 9.38937 15.0663 9.30317 15.1047C9.21696 15.1431 9.12365 15.1629 9.02929 15.1629ZM4.24062 8.17084L9.02929 13.4829L13.8184 8.17084H12.1365C11.9578 8.17084 11.7864 8.09985 11.6601 7.97348C11.5337 7.84711 11.4627 7.67572 11.4627 7.49701V1.34766H6.59767V7.49701C6.59767 7.67572 6.52668 7.84711 6.40031 7.97348C6.27394 8.09985 6.10255 8.17084 5.92384 8.17084H4.24062Z" fill="black"/>
						<path d="M15.1256 18.0586H2.9334C2.15575 18.0577 1.41018 17.7485 0.86025 17.1986C0.310325 16.6488 0.000951249 15.9033 0 15.1256V13.4109C0 13.2322 0.0709924 13.0608 0.19736 12.9345C0.323727 12.8081 0.495118 12.7371 0.673828 12.7371C0.852538 12.7371 1.02393 12.8081 1.1503 12.9345C1.27666 13.0608 1.34766 13.2322 1.34766 13.4109V15.1256C1.34825 15.546 1.51552 15.9489 1.81279 16.2461C2.11006 16.5433 2.51306 16.7104 2.9334 16.7109H15.1256C15.5459 16.7104 15.9489 16.5433 16.2461 16.2461C16.5433 15.9489 16.7105 15.5459 16.7109 15.1256V13.4109C16.7109 13.2322 16.7819 13.0608 16.9083 12.9345C17.0347 12.8081 17.2061 12.7371 17.3848 12.7371C17.5635 12.7371 17.7349 12.8081 17.8612 12.9345C17.9876 13.0608 18.0586 13.2322 18.0586 13.4109V15.1256C18.0576 15.9032 17.7483 16.6486 17.1985 17.1985C16.6487 17.7483 15.9032 18.0576 15.1256 18.0586Z" fill="black"/>
					</svg>
				</div>
			</div>
		</div>
		<button @click="corectareText">
			<svg width="28" height="20" viewBox="0 0 28 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path
					d="M12 13C11.7348 13 11.4804 13.1054 11.2929 13.2929C11.1054 13.4804 11 13.7348 11 14V18H2V2H11V6C11 6.26522 11.1054 6.51957 11.2929 6.70711C11.4804 6.89464 11.7348 7 12 7C12.2652 7 12.5196 6.89464 12.7071 6.70711C12.8946 6.51957 13 6.26522 13 6V1C13 0.734784 12.8946 0.48043 12.7071 0.292893C12.5196 0.105357 12.2652 0 12 0H1C0.734784 0 0.48043 0.105357 0.292893 0.292893C0.105357 0.48043 0 0.734784 0 1V19C0 19.2652 0.105357 19.5196 0.292893 19.7071C0.48043 19.8946 0.734784 20 1 20H12C12.2652 20 12.5196 19.8946 12.7071 19.7071C12.8946 19.5196 13 19.2652 13 19V14C13 13.7348 12.8946 13.4804 12.7071 13.2929C12.5196 13.1054 12.2652 13 12 13Z"
					fill="black" />
				<path
					d="M27 0H16C15.7348 0 15.4804 0.105357 15.2929 0.292893C15.1054 0.48043 15 0.734784 15 1V6C15 6.26522 15.1054 6.51957 15.2929 6.70711C15.4804 6.89464 15.7348 7 16 7C16.2652 7 16.5196 6.89464 16.7071 6.70711C16.8946 6.51957 17 6.26522 17 6V2H26V18H17V14C17 13.7348 16.8946 13.4804 16.7071 13.2929C16.5196 13.1054 16.2652 13 16 13C15.7348 13 15.4804 13.1054 15.2929 13.2929C15.1054 13.4804 15 13.7348 15 14V19C15 19.2652 15.1054 19.5196 15.2929 19.7071C15.4804 19.8946 15.7348 20 16 20H27C27.2652 20 27.5196 19.8946 27.7071 19.7071C27.8946 19.5196 28 19.2652 28 19V1C28 0.734784 27.8946 0.48043 27.7071 0.292893C27.5196 0.105357 27.2652 0 27 0Z"
					fill="black" />
				<path
					d="M5 10C5 10.2652 5.10536 10.5196 5.29289 10.7071C5.48043 10.8946 5.73478 11 6 11H20.59L20.29 11.29C20.1963 11.383 20.1219 11.4936 20.0711 11.6154C20.0203 11.7373 19.9942 11.868 19.9942 12C19.9942 12.132 20.0203 12.2627 20.0711 12.3846C20.1219 12.5064 20.1963 12.617 20.29 12.71C20.383 12.8037 20.4936 12.8781 20.6154 12.9289C20.7373 12.9797 20.868 13.0058 21 13.0058C21.132 13.0058 21.2627 12.9797 21.3846 12.9289C21.5064 12.8781 21.617 12.8037 21.71 12.71L23.71 10.71C23.8037 10.617 23.8781 10.5064 23.9289 10.3846C23.9797 10.2627 24.0058 10.132 24.0058 10C24.0058 9.86799 23.9797 9.73728 23.9289 9.61543C23.8781 9.49357 23.8037 9.38296 23.71 9.29L21.71 7.29C21.6168 7.19676 21.5061 7.1228 21.3842 7.07234C21.2624 7.02188 21.1319 6.99591 21 6.99591C20.7337 6.99591 20.4783 7.1017 20.29 7.29C20.1968 7.38324 20.1228 7.49393 20.0723 7.61575C20.0219 7.73757 19.9959 7.86814 19.9959 8C19.9959 8.2663 20.1017 8.5217 20.29 8.71L20.59 9H6C5.73478 9 5.48043 9.10536 5.29289 9.2929C5.10536 9.48043 5 9.73479 5 10Z"
					fill="black" />
			</svg>
		</button>
		<div class="area-region">
			<textarea v-model="correctedText" spellcheck="false" readonly></textarea>
			<div class="bottom">
				<div class="left">
					Total Cuvinte - {{ totalCorrectedWords }}
				</div>
				<div class="right">
					<svg width="23" height="23" viewBox="0 0 23 23" fill="none" xmlns="http://www.w3.org/2000/svg" @click="copyText('outputText')">
						<path d="M13.6562 4.3125H12.9375V7.90625H16.5312V7.1875H13.6562V4.3125Z" fill="black"/>
						<path d="M14.6131 2.875H7.1875V5.03125H5.03125V20.125H15.8125V17.9688H17.9688V6.24414L14.6131 2.875ZM15.0938 19.4062H5.75V5.75H7.1875V17.9688H15.0938V19.4062ZM17.25 17.25H7.90625V3.59375H14.3166L17.25 6.54063V17.25Z" fill="black"/>
					</svg>

					<svg width="19" height="19" viewBox="0 0 19 19" fill="none" xmlns="http://www.w3.org/2000/svg" @click="saveText('outputText')">
						<path d="M9.02929 15.1629C8.93479 15.1627 8.8414 15.1425 8.75518 15.1039C8.66897 15.0652 8.59186 15.0088 8.52886 14.9383L2.22542 7.94803C2.13881 7.85119 2.08203 7.73137 2.06194 7.60301C2.04185 7.47465 2.05929 7.34322 2.11217 7.22454C2.16506 7.10587 2.25112 7.00501 2.36 6.93412C2.46888 6.86323 2.59593 6.82533 2.72585 6.82498H5.25001V0.673828C5.25001 0.495118 5.321 0.323727 5.44737 0.19736C5.57374 0.0709924 5.74513 0 5.92384 0H12.1365C12.3152 0 12.4866 0.0709924 12.613 0.19736C12.7394 0.323727 12.8104 0.495118 12.8104 0.673828V6.82318H15.3332C15.4631 6.82353 15.5902 6.86143 15.699 6.93233C15.8079 7.00322 15.894 7.10407 15.9469 7.22275C15.9997 7.34142 16.0172 7.47286 15.9971 7.60122C15.977 7.72958 15.9202 7.84939 15.8336 7.94623L9.52972 14.9401C9.46656 15.0102 9.38937 15.0663 9.30317 15.1047C9.21696 15.1431 9.12365 15.1629 9.02929 15.1629ZM4.24062 8.17084L9.02929 13.4829L13.8184 8.17084H12.1365C11.9578 8.17084 11.7864 8.09985 11.6601 7.97348C11.5337 7.84711 11.4627 7.67572 11.4627 7.49701V1.34766H6.59767V7.49701C6.59767 7.67572 6.52668 7.84711 6.40031 7.97348C6.27394 8.09985 6.10255 8.17084 5.92384 8.17084H4.24062Z" fill="black"/>
						<path d="M15.1256 18.0586H2.9334C2.15575 18.0577 1.41018 17.7485 0.86025 17.1986C0.310325 16.6488 0.000951249 15.9033 0 15.1256V13.4109C0 13.2322 0.0709924 13.0608 0.19736 12.9345C0.323727 12.8081 0.495118 12.7371 0.673828 12.7371C0.852538 12.7371 1.02393 12.8081 1.1503 12.9345C1.27666 13.0608 1.34766 13.2322 1.34766 13.4109V15.1256C1.34825 15.546 1.51552 15.9489 1.81279 16.2461C2.11006 16.5433 2.51306 16.7104 2.9334 16.7109H15.1256C15.5459 16.7104 15.9489 16.5433 16.2461 16.2461C16.5433 15.9489 16.7105 15.5459 16.7109 15.1256V13.4109C16.7109 13.2322 16.7819 13.0608 16.9083 12.9345C17.0347 12.8081 17.2061 12.7371 17.3848 12.7371C17.5635 12.7371 17.7349 12.8081 17.8612 12.9345C17.9876 13.0608 18.0586 13.2322 18.0586 13.4109V15.1256C18.0576 15.9032 17.7483 16.6486 17.1985 17.1985C16.6487 17.7483 15.9032 18.0576 15.1256 18.0586Z" fill="black"/>
					</svg>
				</div>
			</div>
		</div>

	</main>
</template>

<style>
* {
	margin: 0;
	box-sizing: border-box;
}

body,
html {
	width: 100%;
	height: 100vh;
}

body {
	background-color: #d6d6d6;
}

main {
	width: 100%;
	height: 100vh;

	display: flex;
	justify-content: center;
	align-items: center;

	flex-direction: row;
}

textarea {
	padding: 5%;
	text-align: start;

	height: 90%;
	width: 100%;

	resize: none;
	border: 0;
	border-bottom: 1px solid #9B9B9B;

	outline: none;
}

button {
	margin-right: 48px;
	margin-left: 48px;

	width: 69px;
	height: 69px;

	background: #FFFFFF;
	box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
	border-radius: 7px;

	border: 0;
	outline: none;

	display: flex;
	justify-content: center;
	align-items: center;

	cursor: pointer;
	transition: all .5s ease-in-out;
}

.area-region {
	border-radius: 4px;
	width: 26.6vw;
	height: 57.6vh;

	background: #FFFFFF;
	box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);

	border: 0;
	outline: none;

	display: flex;
	justify-content: center;
	align-items: flex-start;

	flex-direction: column;
}

button:hover {
	transform: scale(1.05);
}

.bottom {
	width: 100%;
	height: 10%;

	display: flex;
	justify-content: center;
	align-items: center;
}

.left {
	height: 100%;
	width: 50%;

	padding-left: 5%;

	display: flex;
	justify-content: flex-start;
	align-items: center;

	font-family: "Segoe UI", sans-serif;
	font-style: normal;
	color: rgb(37, 37, 37);
	font-weight: 600;
	font-size: 0.75rem;
	letter-spacing: 0.2px;
}

.right {
	height: 100%;
	width: 50%;

    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding-right: 5%;

	gap: 5%;
}

.right svg {
	cursor: pointer;
}
</style>

<script lang="ts">

declare interface Data {
	dictionary: { [key: string]: boolean },
	textCorectat: string,
	inputText: string,
	correctedText: string,
	totalWords: number,
	totalCorrectedWords: number
};

import { textDictionar } from './assets/textDictionar';

export default {
	name: 'App',
	data(): Data {
		return {
			dictionary: {},
			textCorectat: '',
			inputText: '',
			correctedText: '',
			totalWords: 0,
			totalCorrectedWords: 0
		};
	},
	setup() {
		return { textDictionar };
	},
	methods: {
		genereazaDictionar() {
			let cuvinte = this.textDictionar.split(/\s+/);

			for (let i = 0; i < cuvinte.length; i++) {
				let cuvant = cuvinte[i].toLowerCase().replace(/[^\w\săîâșț]|[\d]/gi, '');

				if (cuvant !== '') {
					this.dictionary[this.normalizeDiacritics(cuvant)] = true;
				}
			}
		},
		contineDoarLitere(cuvant: string) {
			return /^[\p{L}]+$/u.test(cuvant);
		},
		corectareText() {
			this.correctedText = this.inputText;
			this.correctedText = this.correctedText.replace(/(?<=\S)([.,;:?!()[\]{}])/g, " $1 "); // Adauga un spatiu inainte si dupa caracterele speciale.
			this.correctedText = this.correctedText.replace(/[\s\n]/g, " "); // Sterge liniile noi. 
			this.correctedText = this.correctedText.replace(/\s{2,}/g, " "); // Sterge spatiile duble.

			if (this.correctedText.length > 0) {
				if (this.correctedText.charAt(0) === " ") {
					this.correctedText = this.correctedText.slice(1);
				}
				if (this.correctedText.charAt(this.correctedText.length - 1) === " ") {
					this.correctedText = this.correctedText.slice(0, -1);
				}
			}; // Elimina spatiul de la inceputul si sfarsitul textului.

			let cuvinte = this.correctedText.split(" ");
			let textCorectat = "";

			for (let i = 0; i < cuvinte.length; i++) {
				let cuvant = cuvinte[i].toLowerCase().replace(/[^\w\sșțâăî]]]|[\d]/gi, '');

				if (!this.contineDoarLitere(cuvant)) {
					textCorectat += cuvinte[i];
					continue;
				};

				if (this.dictionary[this.normalizeDiacritics(cuvant)]) {
					textCorectat += cuvinte[i];
				} else {
					let cuvantCorectat = this.corecteazaCuvant(cuvant);
					textCorectat += cuvantCorectat;
				};

				if (i < cuvinte.length - 1) {
					textCorectat += " ";
				};
			};

			let regex = /(\s*)([.,;:?!()\[\]{}])(\s*)/g;
			let rezultat = textCorectat.replace(regex, function(match, before, punct, after) {
				var spaceBefore = before.length > 0 ? '' : ' ';
				var spaceAfter = after.length > 0 ? '' : ' ';
				return spaceBefore + punct + spaceAfter;
			});

			regex = /(^|[.!?]\s+)([a-zăâîșț])/g;
			rezultat = rezultat.replace(regex, function(match, separator, litera) {
				return separator + litera.toUpperCase();
			});

			rezultat = rezultat.replace(/\s{2,}/g, " ");

			this.correctedText = rezultat;

			this.countCorrectedWords();
		},
		normalizeDiacritics(text: string) {
			return text.normalize("NFD").replace(/[\u0300-\u036f]/g, "");
		},
		countWords() {
			this.totalWords = this.inputText.match(/\s+/g)?.length || 0;

			if (this.inputText == '') {
				this.totalWords = 0;
			};
		},
		copyText(type: string = 'inputArea') {
			if (type == 'inputArea') {
				navigator.clipboard.writeText(this.inputText);
			} else {
				navigator.clipboard.writeText(this.correctedText);
			}
		},
		saveText(type: string = 'inputArea') {
			if (type == 'inputArea') {
				const link = document.createElement("a");
				const file = new Blob([this.inputText], { type: 'text/plain' });

				link.href = URL.createObjectURL(file);
				link.download = "input.txt";
				link.click();
				URL.revokeObjectURL(link.href);
			} else {
				const link = document.createElement("a");
				const file = new Blob([this.correctedText], { type: 'text/plain' });

				link.href = URL.createObjectURL(file);
				link.download = "output.txt";
				link.click();
				URL.revokeObjectURL(link.href);
			}
		},
		countCorrectedWords() {
			this.totalCorrectedWords = this.correctedText.match(/\s+/g)?.length || 0;

			if (this.correctedText == '') {
				this.totalCorrectedWords = 0;
			};
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
		}
	},
	mounted() {
		this.genereazaDictionar();
	}
};
</script>
