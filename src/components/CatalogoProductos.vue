<template>

  <div class="catalogo">
    <!-- Header with navigation buttons, logo, and search box -->
    <header class="header navbar navbar-expand-lg navbar-dark bg-secondary rounded">
      <!-- Left side: container for logo and navigation buttons -->
      <div class="header-left">
        <img
          src="https://s3-alpha-sig.figma.com/img/071b/a995/8a49b93352032fe1c4a5eba14b1a0004?Expires=1743984000&Key-Pair-Id=APKAQ4GOSFWCW27IBOMQ&Signature=DygxQOyZkotrnLrvP51MvCRLtTeaKOKEGNDUdJtlRzw0wCVFesG3hOTbdfJ9Rb8BLD0v3TeBxulPYXkCsEWL7LyBWoNh6QmpIxrnsORBtF~ZuntCgnKzgBS2iYcIReKvc4uFPQdSbBb7I2imaIoPel2LvrsbwVa8R~AHmRty-j-W6l7tg8li6Sbh7OsDuUI5898jD78wDfiA4~yEY9~kOQVLZ8NTmbfGASaSFNVPM1qFmrWZfkamitBLLf8SzAV8Y-7mqQC1vVH5QDaGXkBG44uKqw7TYoIm3q8e71A7a~gxd54CsYr6yeqKeP294p9fjFy5T7mml4idP17KAVL5lw__"
          alt="logo"
          id="logo"
          class="navbar-brand"
        />
        <div class="header-buttons">
          <button class="header-button" id="Inicio_button" onclick="window.location.href='https://RefereeSports.com/inicio';">
            Inicio
          </button>
          <button class="header-button active" id="Catalogo_button" onclick="window.location.href='https://RefereeSports.com/Catalogo';">
            Catálogo
          </button>
        </div>
    
      </div>
        <!-- Right side: search box -->
        <div class="search-box">
  <button class="btn-search">
    <i class="fas fa-search"></i> <!-- Font Awesome icon -->
  </button>
  <input type="text" class="input-search" placeholder="Type to Search...">
</div>


    </header>

    <!-- Filters as buttons -->
    <div class="filtros-container">
  <button class="scroll-btn left" @click="scrollLeft">◀</button>
  <div class="filtros my-3">
    <div class="btn-group" role="group">
      <button
        v-for="genero in generos"
        :key="genero"
        type="button"
        class="btn filtro-boton"
        :class="{ activo: filtroSeleccionado.generos.includes(genero) }"
        @click="alternarFiltro('generos', genero)"
      >
        <span v-if="filtroSeleccionado.generos.includes(genero)">✔</span>
        {{ genero }}
      </button>
    </div>
    <div class="btn-group my-2" role="group">
      <button
        v-for="edad in edades"
        :key="edad"
        type="button"
        class="btn filtro-boton"
        :class="{ activo: filtroSeleccionado.edades.includes(edad) }"
        @click="alternarFiltro('edades', edad)"
      >
        <span v-if="filtroSeleccionado.edades.includes(edad)">✔</span>
        {{ edad }}
      </button>
    </div>
    <div class="btn-group my-2" role="group">
      <button
        v-for="equipo in equipos"
        :key="equipo"
        type="button"
        class="btn filtro-boton"
        :class="{ activo: filtroSeleccionado.equipos.includes(equipo) }"
        @click="alternarFiltro('equipos', equipo)"
      >
        <span v-if="filtroSeleccionado.equipos.includes(equipo)">✔</span>
        {{ equipo }}
      </button>
    </div>
  </div>
  <button class="scroll-btn right" @click="scrollRight">▶</button>
</div>


    <!-- Product list -->
    <div class="row productos">
      <div
        v-for="producto in productosFiltrados"
        :key="producto.id"
        class="col-md-4"
      >
        <div class="card">
          <img
            :src="producto.imagen"
            :alt="producto.titulo"
            class="card-img-top"
          />
          <div class="card-body">
            <h5 class="card-title">{{ producto.titulo }}</h5>
            <p class="card-text">${{ producto.precio }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      busqueda: "",
      generos: ["Masculino", "Femenino"],
      edades: ["Adultos", "Jóvenes"],
      equipos: ["Liga MX", "MLS","america","pumas","chivas","rayados","tigres","cruz azul"],
      filtroSeleccionado: {
        generos: [],
        edades: [],
        equipos: []
      },
      productos: [
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 1,
          titulo: "Jersey Equipo A",
          precio: 150,
          genero: "Masculino",
          edad: "Adultos",
          equipo: "Liga MX",
          imagen: "https://picsum.photos/200/200"
        },
        {
          id: 2,
          titulo: "Jersey Equipo B",
          precio: 120,
          genero: "Femenino",
          edad: "Jóvenes",
          equipo: "MLS",
          imagen: "https://picsum.photos/200/200"
        }
      ],
      productosFiltrados: []
    };
  },
  methods: {
    scrollLeft() {
    const container = this.$el.querySelector('.filtros');
    container.scrollBy({ left: -200, behavior: 'smooth' });
  },
  scrollRight() {
    const container = this.$el.querySelector('.filtros');
    container.scrollBy({ left: 200, behavior: 'smooth' });
  },
    filtrarProductos() {
      this.productosFiltrados = this.productos.filter((producto) => {
        return (
          (this.filtroSeleccionado.generos.length === 0 ||
            this.filtroSeleccionado.generos.includes(producto.genero)) &&
          (this.filtroSeleccionado.edades.length === 0 ||
            this.filtroSeleccionado.edades.includes(producto.edad)) &&
          (this.filtroSeleccionado.equipos.length === 0 ||
            this.filtroSeleccionado.equipos.includes(producto.equipo)) &&
          (this.busqueda === "" ||
            producto.titulo.toLowerCase().includes(this.busqueda.toLowerCase()))
        );
      });
    },
    alternarFiltro(categoria, valor) {
      const index = this.filtroSeleccionado[categoria].indexOf(valor);
      if (index === -1) {
        this.filtroSeleccionado[categoria].push(valor);
      } else {
        this.filtroSeleccionado[categoria].splice(index, 1);
      }
      this.filtrarProductos();
    }
  },
  created() {
    this.filtrarProductos();
  }
};
</script>

<style scoped>
/* Header styles */
.header-left {
  display: flex;
  align-items: center;
  flex-shrink: 0;
  gap: 1em;
}
.header-buttons {
  display: flex;
  gap: 1em;
}
.header-button {
  background: transparent;
  border: 2px solid transparent;
  font-size: 1.8em;
  color: #000;
  padding: 0.5em 1em;
  text-align: left;
  transition: border-color 0.3s ease, box-shadow 0.3s ease, transform 0.2s ease;
}
.header-button.active {
  color: #000;
  font-weight: bold;
}
.header-button:hover {
  border-color: rgba(0, 0, 0, 0.5);
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}
.header-button:active {
  transform: scale(0.95);
  background-color: gray;
}
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0;
  padding: 10px;
  box-shadow: 0px 5px 10px 0px rgba(0, 0, 0, 0.5);
  background-color: #f8f9fa;
}

/* Filters styles */
.filtro-boton {
  background-color: #ccc;
  border: none;
  color: black;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 50px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.404);
}
.filtro-boton:hover {
  background-color: #bbb;
  transform: scale(1.05);
}
.filtro-boton.activo {
  background-color: #444;
  color: white;
}
.filtro-boton:active {
  transform: scale(0.95);
}
.filtro-boton span {
  font-size: 14px;
  margin-right: 8px;
}

/* Product styles */
.productos {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
}
.card {
  box-shadow: 3px 3px 4px 2px rgba(0, 0, 0, 0.404);
  border-radius: 8px;
  transition: box-shadow 0.3s ease;
}
.card:hover {
  box-shadow: 10px 22px 15px rgba(0, 0, 0, 0.685);
}
.card-body {
  padding: 2px;
  text-align: center;
  background-color: #fff;
  border-radius: 8px;
}
.card-title {
  font-size: 1.5em;
  margin-bottom: 5px;
}
.card img {
  max-width: 100%;
  height: auto;
}

/* Search box styles */
.search-box {
  width: fit-content;
  height: fit-content;
  position: relative;
}
.input-search {
  height: 50px;
  width: 50px;
  border-style: none;
  padding: 10px;
  font-size: 18px;
  letter-spacing: 2px;
  outline: none;
  border-radius: 25px;
  transition: all 0.5s ease-in-out;
  background-color: #c7c7c7;
  padding-right: 40px;
  color: #000000;
}
.input-search::placeholder {
  color: rgba(0, 0, 0, 0.5);
  font-size: 18px;
  letter-spacing: 2px;
  font-weight: 100;
}
.input-search:focus {
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom: 1px solid #c7c7c7;
  transition: all 500ms cubic-bezier(0, 0.11, 0.35, 2);
}
.btn-search {
  width: 50px;
  height: 50px;
  border-style: none;
  font-size: 20px;
  font-weight: bold;
  outline: none;
  cursor: pointer;
  border-radius: 50%;
  position: absolute;
  right: 0px;
  color: #000000;
  background-color: transparent;
}
.btn-search:focus ~ .input-search {
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom: 1px solid rgba(0, 0, 0, 0.5);
  transition: all 500ms cubic-bezier(0, 0.11, 0.35, 2);
}

/* General styles */
body {
  margin: 0px;
  padding: 0px;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #c7c7c7;
  font-family: 'Lato' !important;
}
* {
  box-sizing: border-box;
}


.navbar-brand{
    width: 100px; /* Ajusta el tamaño del logo según sea necesario */
    height: auto; /* Mantiene la proporción del logo */
    margin-right: 10px; /* Espacio entre el logo y los botones */
}
.filtros{
    display: flex;
    align-items: center;
    margin-top: 20px;
    align-content: center;
    gap: 10px;
    margin-bottom: 20px;
}
.btn-group{
    display: flex;
    gap: 10px;
}
.filtros-container {
  display: flex;
  align-items: center;
  position: relative;
}

.scroll-btn {
  background-color: #ccc;
  border: none;
  color: black;
  padding: 10px;
  font-size: 18px;
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s;
}

.scroll-btn:hover {
  background-color: #bbb;
}

.scroll-btn.left {
  margin-right: 10px;
}

.scroll-btn.right {
  margin-left: 10px;
}

.filtros {
  display: flex;
  overflow-x: auto; /* Enables horizontal scrolling */
  white-space: nowrap; /* Prevents wrapping */
  gap: 10px; /* Space between buttons */
  scrollbar-width: none; /* Hides the scrollbar */
margin-bottom: 20px;
}

.filtros::-webkit-scrollbar {
  display: none; /* Hides scrollbar for Webkit browsers */
}

</style>
