![tetris](https://user-images.githubusercontent.com/110226567/214046509-0830e026-5866-43a5-b70c-141eeeb517ba.png)

# π§± Tetris

μΆμ΅μ ννΈλ¦¬μ€ κ²μ π [Demo](https://imjone.github.io/tetris/)

<br />

## π’ νλ‘μ νΈ κ°μ

μλ λννλ λΈλ‘μ μμ§μ¬μ μμλκ°λ κ²μμλλ€.<br />
λΈλ‘μ΄ κ°λ‘λ‘ κ½ μ±μμ§λ©΄ ν΄λΉ λΌμΈμ΄ μ¬λΌμ§κ³  μ μκ° 1μ  μΆκ°λλ©°,<br />
λΈλ‘μ΄ λ§¨ μκΉμ§ μμ¬μ μΈλ‘λ‘ κ½ μ±μμ§λ©΄ κ·Έ μ¦μ κ²μμ΄ μ’λ£λ©λλ€.

<br />

## π¨οΈ μ¬μ© κΈ°μ 

<p>
 <img src="https://img.shields.io/badge/HTML-e34f26?style=flat-square&logo=HTML5&logoColor=white" />
 <img src="https://img.shields.io/badge/CSS-1572b6?style=flat-square&logo=CSS3&logoColor=white" />
 <img src="https://img.shields.io/badge/JavaScript-f7df1e?style=flat-square&logo=JavaScript&logoColor=white" />
</p>

<br />

## π μ£Όμ κΈ°λ₯

- λ¬΄μμ λΈλ‘ μμ± λ° λ λλ§
- κ²μ μ§ν μκ°μ΄ κΈ°λ‘λλ νμ΄λ¨Έ
- λ°©ν₯ν€λ₯Ό ν΅ν λΈλ‘ μ΄λ λ° λͺ¨μ λ³κ²½
- λ©μΈ νμ΄μ§ μ΄λ λ° λ€μ μμ λ²νΌ
- κ²μ μ’λ£ μ κ²°κ³Ό νμμ°½ λΈμΆ

<br />

## π» μμ€ μ½λ

μ μ²΄ μ½λ λ³΄λ¬ κ°κΈ° π [Notion](https://imjone.notion.site/Tetris-2d36893b850046a882a20f1f0451a029)

### π λΈλ‘ λ°°μ΄ μ μ

`BLOCKS` λΌλ κ°μ²΄ μμ λͺ¨λ  λΈλ‘μ λͺ¨μμ μ€μ²© λ°°μ΄λ‘ μ μν΄λμμ΅λλ€.<br />
μ΄ λ κ° λ°°μ΄μ μμλ κ²©μνμμ ν΄λΉ λΈλ‘μ΄ μ°¨μ§ν  μ’νλ₯Ό μλ―Έν©λλ€.

```javascript
const BLOCKS = {
  square: [
    [[0, 0],[0, 1],[1, 0],[1, 1]],
    [[0, 0],[0, 1],[1, 0],[1, 1]],
    [[0, 0],[0, 1],[1, 0],[1, 1]],
    [[0, 0],[0, 1],[1, 0],[1, 1]]
  ],
  zee: [
    [[0, 0],[1, 0],[1, 1],[2, 1]],
    [[0, 1],[1, 0],[1, 1],[0, 2]],
    [[0, 1],[1, 1],[1, 2],[2, 2]],
    [[2, 0],[2, 1],[1, 1],[1, 2]]
  ],
  ...
};

export default BLOCKS;
```

### π λ¬΄μμ λΈλ‘ μμ±

`Math.floor`λ₯Ό ν΅ν΄ `BLOCKS` λ°°μ΄ μμμ λ¬΄μμλ‘ μλ‘μ΄ λΈλ‘μ΄ μμ±λ©λλ€.<br />
`tempMovingItem`μ λΈλ‘ μμ± λ° λ λλ§ λ¨κ³μμ μ κΉ μ°μ΄λ μμ λ³μμ΄λ©°,<br />
μ΄ λ€μ λΈλ‘μ΄ μμ±λ  λλ₯Ό λλΉν΄μ `tempMovingItem`μ μ΄κΈ°νμμΌ μ€λλ€.

```javascript
let tempMovingItem;
const movingItem = {
  type: '',
  direction: 3,
  top: 0,
  left: 0,
};

function generateNewBlock() {
  const blockArray = Object.entries(BLOCKS);
  const randomIndex = Math.floor(Math.random() * blockArray.length);

  movingItem.type = blockArray[randomIndex][0]; // λλ€ν λͺ¨μμ λΈλ­ μμ±
  movingItem.top = 0;
  movingItem.left = 3;
  movingItem.direction = 0;
  tempMovingItem = { ...movingItem }; // μ΄κΈ°ν ν μλ‘μ΄ λΈλ­ μμ±
  renderBlocks();
}
```

### π λΈλ‘ μ΄λ λ° λͺ¨μ λ³κ²½

`keydown` μ΄λ²€νΈλ₯Ό ν΅ν΄ μλ ₯ν ν€μ λ°λΌ λΈλ‘μ λ°©ν₯ λ° λͺ¨μμ μ μ΄ν©λλ€.<br />
`moveBlock` - μ΄λν  λ°©ν₯μ μΈμλ‘ μ λ¬ λ°μ ν λΆλ‘μ ν μΉΈμ© μ΄λμν΅λλ€.<br />
`changeDirection` - `BLOCKS` λ°°μ΄μ μ μλ μμλλ‘ λΈλ‘μ λͺ¨μμ΄ λ¨κ³μ μΌλ‘ λ³κ²½λ©λλ€.

```javascript
function moveBlock(moveType, amount) {
  tempMovingItem[moveType] += amount; // left, top
  renderBlocks(moveType);
}

function changeDirection() {
  const direction = tempMovingItem.direction;
  direction === 3 ? (tempMovingItem.direction = 0) : (tempMovingItem.direction += 1);
  renderBlocks();
}

document.addEventListener('keydown', e => {
  switch (e.key) {
    case 'ArrowRight':
      moveBlock('left', 1);
      break;
    case 'ArrowLeft':
      moveBlock('left', -1);
      break;
    case 'ArrowDown':
      moveBlock('top', 1);
      break;
    case 'ArrowUp':
      changeDirection();
      break;
    case ' ': // space bar
      dropBlock();
      break;
    default:
      break;
  }
});
```

<br />

## π λ°°μ΄ μ  λ° λλ μ 

- κΈ°λ₯μ ν¨μ λ¨μλ‘ μ?μ΄λκ°λ μ°μ΅μ ν΄λ³Ό μ μμ΄ μ λ§ μλ―Έ μλ νλ‘μ νΈμμ΅λλ€.
- λΈλ‘μ λͺ¨μμ λ°°μ΄λ‘ μ μν¨μΌλ‘μ¨ λ°°μ΄μ νμ©λκ° μ λ§ λλ€λ κ²μ λ€μ νλ² κΉ¨λ¬μμ΅λλ€.
- ν΄λμ€ λ¬Έλ²μ λ₯μνκ² μ¬μ©ν  μ μλλ‘ λμ± μμ£Ό μ¬μ©ν΄λ΄μΌκ² λ€κ³  λκΌμ΅λλ€.
- λ€μμ λμ¬ λΈλ‘μ λ―Έλ¦¬ λ³΄μ¬μ£Όλ κΈ°λ₯μ κ΅¬ννμ§ λͺ»ν κ²μ λν΄ μμ¬μμ΄ λ§μ΄ λ¨μ΅λλ€.
