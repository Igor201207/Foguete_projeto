// ===== PLANETAS (CICLO) =====
const planetas = [
    document.querySelector(".clouds"),
    document.querySelector(".planeta"),
    document.querySelector(".planeta2")
]

const duracao = 12000

function iniciarCiclo() {

    planetas.forEach((planeta, index) => {

        setTimeout(() => {
            planeta.style.animation = "none"
            planeta.offsetHeight

            planeta.style.animation = `mover 12s linear forwards`
        }, index * duracao)

    })

    setTimeout(iniciarCiclo, planetas.length * duracao)
}

iniciarCiclo()


// ===== FOGUETE =====
const foguete = document.getElementById("foguete")
const espaco = document.getElementById("espaco")

let posX = 10
let posY = 45
const velocidade = 0.5

const teclas = {}

document.addEventListener("keydown", (e) => {
    teclas[e.key.toLowerCase()] = true
})

document.addEventListener("keyup", (e) => {
    teclas[e.key.toLowerCase()] = false
})


// ===== IA (AUTO PILOTO) =====
let modoIA = false

document.addEventListener("keydown", (e) => {
    if(e.key === "i"){
        modoIA = !modoIA
        console.log("IA:", modoIA ? "ATIVADA 🤖" : "DESATIVADA 🎮")
    }
})

function IA(){

    const meteoros = document.querySelectorAll(".meteoro")

    meteoros.forEach(meteoro => {

        const r1 = foguete.getBoundingClientRect()
        const r2 = meteoro.getBoundingClientRect()

        // Só reage se estiver MUITO perto
        if(r2.left < r1.right + 80){

            // chance de errar (IA não perfeita 😈)
            if(Math.random() < 0.3) return

            if(r2.top < r1.top){
                posY += 0.7
            } else {
                posY -= 0.7
            }
        }

    })
}


// ===== ATUALIZAÇÃO =====
function atualizar(){

    if(modoIA){
        IA()
    } else {
        // Movimento manual
        if(teclas["w"] || teclas["arrowup"]) posY -= velocidade
        if(teclas["s"] || teclas["arrowdown"]) posY += velocidade
        if(teclas["a"] || teclas["arrowleft"]) posX -= velocidade
        if(teclas["d"] || teclas["arrowright"]) posX += velocidade
    }

    // Limites
    posX = Math.max(0, Math.min(90, posX))
    posY = Math.max(0, Math.min(90, posY))

    foguete.style.left = posX + "%"
    foguete.style.top = posY + "%"

    requestAnimationFrame(atualizar)
}

atualizar()


// ===== METEOROS =====
function criarMeteoro(){

    const meteoro = document.createElement("div")
    meteoro.classList.add("meteoro")

    meteoro.style.left = "100%"
    meteoro.style.top = Math.random() * 90 + "%"

    espaco.appendChild(meteoro)

    let pos = 100
    let velocidadeMeteoro = 0.3

    function mover(){

        pos -= velocidadeMeteoro
        meteoro.style.left = pos + "%"

        // IA do meteoro (segue o jogador levemente)
        let alvoY = posY
        let atualY = parseFloat(meteoro.style.top)

        if(atualY < alvoY){
            meteoro.style.top = atualY + 0.2 + "%"
        } else {
            meteoro.style.top = atualY - 0.2 + "%"
        }

        // Colisão
        if(colidiu(foguete, meteoro)){
            alert("💥 Você perdeu!")
            reiniciarJogo()
        }

        if(pos < -10){
            meteoro.remove()
        } else {
            requestAnimationFrame(mover)
        }
    }

    mover()
}

setInterval(criarMeteoro, 2000)


// ===== COLISÃO =====
function colidiu(a, b){

    const r1 = a.getBoundingClientRect()
    const r2 = b.getBoundingClientRect()

    const margem = 20 // 🔥 diminui a área de colisão

    return !(
        r1.top + margem > r2.bottom - margem ||
        r1.bottom - margem < r2.top + margem ||
        r1.right - margem < r2.left + margem ||
        r1.left + margem > r2.right - margem
    )
}

function reiniciarJogo(){

    // remove meteoros
    document.querySelectorAll(".meteoro").forEach(m => m.remove())

    // reseta posição do foguete
    posX = 10
    posY = 45

    foguete.style.left = posX + "%"
    foguete.style.top = posY + "%"

}
