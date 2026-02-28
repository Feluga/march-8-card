<script>
export default {
    data() {
        return {
            isDark: false,
            currentPhrase: 'Нажми на кнопку, чтобы получить фразу',
            phrases: [
                "Пусть весна цветет не только на улице, но и в душе! 🌷",
                "Сияй, люби и будь самой счастливой! ✨",
                "Меньше дедлайнов, больше тюльпанов и отдыха! 💐",
                "Ты — главное украшение этой весны! 💖",
                "Пусть каждый день дарит повод для улыбки! 🎀",
                "Пусть эта весна принесёт море вдохновения и нежности! 🌸",
                "Желаю, чтобы в твоём сердце всегда жила весна и любовь! 💖",
                "Будь дерзкой в своих мечтах и нежной в каждом моменте! ✨",
                "Пусть каждый твой день будет ярким, как букет весенних цветов! 💐",
                "Ты вдохновляешь этот мир просто тем, что ты в нем есть! 🌷",
                "Желаю сиять ярче любого хайлайтера! ✨"
            ]
        }
    },

    methods: {
        generate() {
            const randomIndex = Math.floor(Math.random() * this.phrases.length)
            const newPhrase = this.phrases[randomIndex]
            // Логика проверки на повтор
            if (newPhrase === this.currentPhrase) {
                this.generate()
            } else {
                this.currentPhrase = newPhrase
            }
        },
        copyText() {
            navigator.clipboard.writeText(this.currentPhrase);
        }
    }
}
</script>

<template>
    <div class="card">
        <h2>🌸 Поздравление 🌸</h2>
        <div class="phrase-container">
            <transition name="fade" mode="out-in">
                <p :key="currentPhrase">{{ currentPhrase }}</p>
            </transition>
        </div>
        <div class="between">
            <button @click="generate">Сгенерировать ✨</button>
            <button @click="copyText">📋</button>
        </div>
    </div>
</template>

<style>
body {
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #212121;
}

.card {
    background: #ffffff;
    padding: 2rem;
    border-radius: 24px;
    text-align: center;
    width: 90%;
    border: 4px solid transparent;
    background-image:
        linear-gradient(white, white),
        linear-gradient(135deg, #833ab4, #fd1d1d, #fcb045, #833ab4);
    background-size: 100% 100%, 300% 300%;
    animation: border-dance 4s linear infinite;
    background-clip: padding-box, border-box;
    background-origin: border-box;
    box-shadow: 0 10px 30px rgba(255, 0, 127, 0.5);
    font-family: 'Raleway', sans-serif;

}

.between {
    display: flex;
    justify-content: space-around;
    align-items: center;
}

.phrase-container {
    height: 150px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 20px 0;
}

p {
    font-size: 1.3rem;
    color: #000000;
    line-height: 1.5;
}

button {
    background: linear-gradient(135deg, #ff7eb3, #ff5975);
    color: rgb(255, 255, 255);
    border: none;
    padding: 14px 28px;
    border-radius: 12px;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    font-family: 'Raleway', sans-serif;
}

button:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(255, 117, 140, 0.4);
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}

@keyframes border-dance {
    0% {
        background-position: 0% 0%, 0% 50%;
    }

    50% {
        background-position: 0% 0%, 100% 50%;
    }

    100% {
        background-position: 0% 0%, 0% 50%;
    }
}



@media (max-width: 600px) {
    .card {
        width: 90% !important;
        /* Заставит карточку сжаться */
        max-width: 350px !important;
        padding: 1.2rem !important;
    }

    .actions {
        flex-direction: column !important;
        /* Кнопки встанут друг под другом */
        gap: 15px !important;
    }

    button {
        width: 100% !important;
        /* Кнопки станут на всю ширину */
    }
}
</style>