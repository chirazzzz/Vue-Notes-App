<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum fuga
            tenetur at blanditiis perferendis accusamus!
          </p>
          <p class="date">04/07/6521</p>
        </div>
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum fuga
            tenetur at blanditiis perferendis accusamus!
          </p>
          <p class="date">04/07/6521</p>
        </div>
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum fuga
            tenetur at blanditiis perferendis accusamus!
          </p>
          <p class="date">04/07/6521</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}

.container {
  max-width: 1000px;
  padding: 0.625em; /* 10px */
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

h1 {
  font-weight: bold;
  margin-bottom: 1.5em; /* 24px */
  font-size: 4.5rem; /* 72px */
}

button {
  border: none;
  padding: 0.625em; /* 10px */
  width: 2.5em; /* 40px */
  height: 2.5em; /* 40px */
  cursor: pointer;
  background: rgba(21, 20, 20);
  border-radius: 100%;
  color: white;
  font-size: 1.25rem; /* 20px */
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
}

.card {
  width: 14em; /* 224px */
  height: 14em; /* 224px */
  background: rgba(237, 182, 44);
  padding: 0.625em; /* 10px */
  margin: 0 1.25em 1.25em 0;
  border-radius: 1em; /* 16px */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-size: 0.875rem;
}

.date {
  font-size: 0.5rem;
  font-weight: bold;
  letter-spacing: 1px;
}
</style>
