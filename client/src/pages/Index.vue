<template>
  <Layout>
    Hey
    <ul v-for="(offering, idx) in offerings">
      <li>
        <div>
          <h1>
            {{ offering.Title }}
          </h1>
          <p>{{ offering.Description }}</p>
          <span>${{ offering.Price }}</span>
        </div>
      </li>
    </ul>
  </Layout>
</template>

<page-query>
query {
  offerings: allStrapiOfferings {
    edges {
      node {
        id
        Title,
        Image{
          url
        },
        Description,
        Price
      }
    }
  }
}
</page-query>

<script>
export default {
  name: "Home",
  metaInfo: {
    title: "Hello, world!",
  },
  computed: {
    offerings() {
      return this.$page.offerings.edges.map((offering) => {
        return { ...offering.node };
      });
    },
  },
};
</script>
