# Ejercicios

1. Crear un servidor que exponga a través de Websockets los cambios en los partidos de futbol y mostrarlos en un index.html.
```javascript
let matches = [
  {
    local: 'Real Madrid',
    away: 'Sevilla',
    time: 945,
    localGoals: 2,
    awayGoals: 0,
  },
  {
    local: 'Espanyol',
    away: 'Betis',
    time: 1412,
    localGoals: 0,
    awayGoals: 0,
  },
   {
    local: 'Barcelona',
    away: 'Getafe',
    time: 746,
    localGoals: 1,
    awayGoals: 0,
  }
]

const updateTime = matches => matches.map(match => {
  ++match.time
  return match
})

const updateGoals = matches => matches.map(match => {
  let randomNumber = Math.floor(Math.random() * 2) + 1
  if (randomNumber === 1) {
    ++match.localGoals
  } else {
    ++match.awayGoals
  }
  return match
})

setInterval(() => {
  matches = updateTime(matches)
  console.log(matches)
}, 1000)

setInterval(() => {
  matches = updateGoals(matches)
  console.log(matches)
}, 5000)
```

