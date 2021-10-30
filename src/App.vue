<template>
  <div id="app">
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img src="/images/logo.png">
        </router-link>
      </div>
      <div id="side">
        <router-link to="/browse">
          <div class="menu-item browse">
            <img src="/images/globe.png">
            <p>Browse</p>
          </div> 
        </router-link>
        <router-link to="/cart">
          <div class="menu-item">
            <img src="/images/love.png">
            <p> {{numItems}} items</p>
          </div>
        </router-link>
      </div>
    </div>
    <router-view/>
    <div class="footer-container">
      <div class="footer">
        <a href="https://github.com/BYUCS260/grocery-store-shiozawt"> MY GITHUB REPO </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
    }
  },
  computed: {
    numItems() {
      return this.$root.$data.cart.length;
    }
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;
}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3등분; 1fr: each one taking equal fraction of width of the screen */
  grid-column-gap: 5px; /* 등분 간의 간격 */
  grid-template-areas: "none brand side"; /* 등분 각각 이름 */
  margin-bottom: 50px;
}

#menu a {
  color: #B84901; /* HTML의 a는 여기에서 router-link를 가리킴 */
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column; /* 이미지와 문자열이 열(column; 위,아래)로 표현되게 함 (default: 옆으로 나란히(row)) */
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}

.footer-container {
  align: center;
  background-color: lightgrey;
  width: 100%;
  height: 50px;
  position: fixed;
  bottom: 0;
  text-align: center;
  padding: 20px;
  margin-right: 100px;
  color: black;
  font: italic small-caps bold 12px/30px Georgia, serif;
}

</style>