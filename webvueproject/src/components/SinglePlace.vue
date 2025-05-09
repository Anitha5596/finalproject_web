<template>
    <div>
      <nav class="menu-bar">
        <div class="menu-header">
          <button class="hamburger" @click="toggleMenu">☰</button>
        </div>
        <ul v-show="menuVisible" class="menu-list">
          <li><a href="#high-rated">⭐ Highly Rated</a></li>
          <li><a href="#other-rated">📍 Other Places</a></li>
          <li><a href="#free-entry">🎫 Free Entry</a></li>
        </ul>
      </nav>
  
     
      <h2 id="high-rated" style="text-align: center;">⭐ Highly Rated Places</h2>
      <div class="grid-container">
        <div
          v-for="place in highRated"
          :key="place.id"
          :class="place.Rating > 4.5 ? 'blue' : 'pink'"
          class="place-card"
        >
          <h3><strong>Place:</strong> {{ place.PlaceName }}</h3>
          <h4><strong>Address:</strong> {{ place.Address }}</h4>
          <p><strong>Visiting Time:</strong> {{ place.VisitingTime }}</p>
          <p><strong>Entry Fee:</strong> {{ place.EntryFee }}</p>
          <p><strong>Rating:</strong> {{ place.Rating }}</p>
        </div>
      </div>
        <h2 id="other-rated" style="text-align: center;">📍 Other Places</h2>
      <div class="grid-container">
        <div
          v-for="place in otherRated"
          :key="place.id"
          :class="place.Rating > 4.5 ? 'blue' : 'pink'"
          class="place-card"
        >
          <h3><strong>Place:</strong> {{ place.PlaceName }}</h3>
          <h4><strong>Address:</strong> {{ place.Address }}</h4>
          <p><strong>Visiting Time:</strong> {{ place.VisitingTime }}</p>
          <p><strong>Entry Fee:</strong> {{ place.EntryFee }}</p>
          <p><strong>Rating:</strong> {{ place.Rating }}</p>
        </div>
      </div>
        <h2 id="free-entry" style="text-align: center;">🎫 Free Entry Places</h2>
      <div class="grid-container">
        <div
          v-for="place in freeEntry"
          :key="place.id"
          :class="place.Rating > 4.5 ? 'blue' : 'pink'"
          class="place-card"
        >
          <h3><strong>Place:</strong> {{ place.PlaceName }}</h3>
          <h4><strong>Address:</strong> {{ place.Address }}</h4>
          <p><strong>Visiting Time:</strong> {{ place.VisitingTime }}</p>
          <p><strong>Entry Fee:</strong> {{ place.EntryFee }}</p>
          <p><strong>Rating:</strong> {{ place.Rating }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      places: {
        type: Array,
        required: true
      }
    },
    data() {
      return {
        menuVisible: true
      };
    },
    mounted() {
      this.menuVisible = window.innerWidth > 768;
      window.addEventListener("resize", () => {
        this.menuVisible = window.innerWidth > 768;
      });
    },
    methods: {
      toggleMenu() {
        this.menuVisible = !this.menuVisible;
      }
    },
    computed: {
      highRated() {
        return this.places.filter(p => p.Rating > 4.5);
      },
      otherRated() {
        const highRatedIds = this.highRated.map(p => p.id);
        return this.places.filter(p => p.Rating <= 4.5 && !highRatedIds.includes(p.id));
      },
      freeEntry() {
        return this.places.filter(
          p =>
            typeof p.EntryFee === "string" &&
            p.EntryFee.trim().toLowerCase() === "free"
        );
      }
    }
  };
  </script>
  
  <style scoped>
.menu-bar {
  background-color: #101111;
  color: white;
  padding: 10px 0;
  position: sticky;
  top: 0;
  z-index: 999;
}
.menu-header {
  display: block;
  padding: 0 20px;
  width: 100%;
  height: 25px;
  position: relative;
}
.hamburger {
  display: none;
  background: none;
  border: none;
  font-size: 26px;
  color: white;
  cursor: pointer;
  position: absolute;
  right: 20px;
  top: 5px;
}

.menu-list {
  list-style: none;
  text-align: center;
  margin: 0;
  padding: 0;
}

.menu-list li {
  display: inline-block;
  margin: 0 20px;
}

.menu-list a {
  color: white;
  text-decoration: none;
  font-size: 28px;
  font-weight: bold;
}

.menu-list a:hover {
  text-decoration: underline;
}

@media (max-width: 768px) {
  .menu-header {
    display: block;
  }

  .hamburger {
    display: inline-block;
  }

  .menu-list {
    display: block;
    background-color: #111112;
    padding-top: 10px;
  }

  .menu-list li {
    display: block;
    margin: 10px 0;
  }
}

.grid-container {
  text-align: center;
  font-size: 0; 
  margin: 20px auto;
  width: 95%;
}

.place-card {
  display: inline-block;
  vertical-align: top;
  width: 280px;
  height: 240px;
  margin: 10px;
  padding: 15px;
  border-radius: 10px;
  font-size: 16px;
  font-family: Arial, sans-serif;
  box-sizing: border-box;
  text-align: left;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
}

.blue {
  background-color: #91ceed;
  color: rgb(2, 2, 2);
}

.pink {
  background-color: #bba5c2;
  color: black;
}

h2, h3, h4 {
  margin-bottom: 6px;
}
</style>

  