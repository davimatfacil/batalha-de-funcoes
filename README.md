# Batalha de Funções ⚔️

Jogo educativo em que **funções matemáticas batalham**. Quando uma função encontra um operador (derivada ou integral), a matemática acontece na tela: x³ → 3x² → 6x → 6 → 0 (a função vira constante e some).

Arquivo único (`index.html`), sem dependências. Basta abrir no navegador.

## Regras

| Colisão | Resultado |
|---|---|
| `d/dx` + função | A função é derivada. Constante → 0 e some. |
| `∫` + função | A função é integrada (sem o `+C`). |
| `d/dx` + `∫` | Se anulam (operações inversas). |
| função + função | Somam-se (opcional). |

Cada operador tem 6 cargas. Funções com grau maior que 7 "explodem". Curiosidades: eˣ é imune à derivada; sen e cos giram em ciclo para sempre.

## Como funciona (para estudar o código)

1. **Função = lista de termos.** Cada termo é `{tipo, expoente, coeficiente}`, com tipo em potência, `sen`, `cos` ou `eˣ`. Esse conjunto é fechado para derivada e integral, então não é preciso uma biblioteca de matemática simbólica.
2. **Regras no código.** `deriv` usa (c·xⁿ)′ = c·n·xⁿ⁻¹ e descarta constantes. `integ` faz o inverso.
3. **Frações exatas.** Coeficientes são frações (com `gcd`), então ∫x² aparece como x³/3.
4. **`simplify`.** Agrupa termos iguais e remove os de coeficiente zero.
5. **Física.** Colisão circular (distância entre centros < soma dos raios), com um tempo de espera para o mesmo par não colidir a cada frame.
6. **Motor separado do visual.** O trecho entre `// ==== MOTOR ====` e `// ==== FIM MOTOR ====` não depende do canvas e pode ser testado em Node.

## Ideias para evoluir

- Novos tipos de termo (`ln x`, `1/x`). Atenção: ∫xⁿ falha em n = −1.
- Duelo por turnos, limites e multiplicação de funções.

Ideia inspirada em um vídeo de @math.vsmath (Instagram).
