<script>
  const products = [
    "BELL PEPPER",
    "TOMATE",
    "AGUACATE",
    "LECHUGA",
    "CEBOLLA",
    "CILANTRO",
    "JALAPEÑO",
    "POBLANO PEPPER",
    "HONGOS",
    "LIMON VERDE",
    "LIMON AMARILLO",
    "HUEVOS",
    "PAPAS",
    "CALABAZA",
    "ESPINACA",
    "TOMATILLO",
    'TORTILLA DE MAIZ "EL MILAGRO"',
    "ZANAHORIA",
    "APIO",
    "COLIFLOR",
    "BROCOLI",
    "CHILE BANANA",
    "CHILE ARBOL",
    "CHILE GUAJILLO",
    "CHILE ANCHO",
    "TAMARINDO",
    "JAMAICA",
    "ARROZ",
    "FRIJOL",
    "AJO MOLIDO",
    "CHILE POWDER",
    "PIMIENTA",
    "COMINO",
    "OREGANO",
    "PEREJIL",
    "LAUREL",
    "SANGRIA",
    "ROOT BEER",
    "PIÑA",
    "JUGO MANZANA EN BOTELLA",
    "TE",
    "CAJAS TO GO 9X9",
    "SASONADOR FAJITAS",
    "PLATOS #",
    "SERVILLETAS 17X17"
  ];

  const productsValue = products.reduce((acc, product) => {
    acc[product] = "";
    return acc;
  }, {});

  $: output = Object.entries(productsValue)
    .filter(([, value]) => value.length > 0)
    .map(([product, value]) => `${value} ${product}`)
    .join("\n");
</script>

<style>
  .product-container {
    padding: 0.25rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 0.5rem;
  }
  .product-container:nth-child(odd) {
    background-color: lightgray;
  }
  .output {
    padding: 0.5rem;
    background-color: yellow;
  }
</style>

<main>
	<article class="products">
  {#each products as product}
    <section class="product-container">
      <input type="text" id={product.toLowerCase().replace(/\s/g, "_")} bind:value={productsValue[product]}>
      <label for={product.toLowerCase().replace(/\s/g, "_")}>{product}</label>
    </section>
  {/each}
  </article>

  <pre class="output">{output}</pre>
</main>