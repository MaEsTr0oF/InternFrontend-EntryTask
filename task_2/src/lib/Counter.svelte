<script lang="ts">
	let flag = false;
	let name1 = 0;
	let name2 = 0;
	let valu = 10;
	function fillSpoilerContent(data: { rates: Record<string, number> }) {
		const spoilerContent = document.getElementById("spoilerContent");
		spoilerContent.innerHTML = ""; // Очищаем содержимое спойлера

		if (data.rates && typeof data.rates === "object") {
			Object.keys(data.rates).forEach((key) => {
				const obj = data.rates[key];
				const objElement = document.createElement("div");
				objElement.textContent = `${key}: ${obj}`;
				spoilerContent.appendChild(objElement);
			});
		} else {
			const errorElement = document.createElement("div");
			errorElement.textContent =
				"Данные о курсах валют отсутствуют или некорректны.";
			spoilerContent.appendChild(errorElement);
		}
	}

	function val(data: { rates: Record<string, number> }) {
		const spoilerContent = document.getElementById("spoilerContent");

		if (spoilerContent.style.display === "none") {
			spoilerContent.style.display = "block";
			fillSpoilerContent(data);
		} else {
			spoilerContent.style.display = "none";
		}
	}

	fetch("https://api.exchangerate-api.com/v4/latest/USD")
		.then((response) => response.json())
		.then((data: { rates: Record<string, number> }) => {
			console.log(data.rates);
			val(data); // Вызываем функцию val() с полученными данными
		})
		.catch((error) => {
			console.error("Ошибка при получении данных:", error);
		});
	document.addEventListener;
	const refresh = () => {
		if (flag == false) {
			flag = true;
		} else {
			flag = false;
		}
	};
	const finall = () => {
		if (flag == false) {
			name2 = name1 * valu;
		} else {
			name1 = name2 * valu;
		}
	};
</script>

<div class="inp">
	<div class="inp__1">
		<input type="text" name="message" class="inpt__1" bind:value={name1} />
	</div>
	<div class="inp__but">
		<button class="fin" id="final" on:click={finall}>конвертировать</button>
		<button class="refre" id="refresh" on:click={refresh}
			><img src="src\папка\image-3.png" alt="" /></button
		>
	</div>
	<div class="inp__1">
		<input type="text" class="inpt__1" id="input2" bind:value={name2} />
	</div>
</div>
<button id="toggleSpoilers">Показать спойлер</button>
<div id="spoilerContent" class="spoiler-content">
	<!-- Здесь будут отображаться объекты из вашего объекта -->
</div>

<style>
	.spoiler-content {
		display: none;
	}
	.inp {
		display: flex;
		justify-content: space-between;
		gap: 30px;
	}
	.inp__but {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 30px;
	}
</style>
