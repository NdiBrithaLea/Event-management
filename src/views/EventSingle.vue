<template>
  <div class="event-single">
    <section class="hero is-primary">
      <div class="hero-head text-white">
        <div class="container">
          <h1 class="title">
            {{ event.name }}
          </h1>
          <h4 class="subtitle ">
            <strong>Date:</strong> {{ event.date }}
            <br>
            <strong>Time:</strong> {{ event.time }}
          </h4>
        </div>
      </div>
    </section>
    <section class="event-content">
      <div class="container">
        <p class="is-size-4 description">{{ event.description }}</p>
        <p class="is-size-5"><strong>Location:</strong> {{ event.location }}</p>
        <p class="is-size-5"><strong>Category:</strong> {{ event.category }}</p>
        <div class="event-images row">
          <div v-for="image in event.images" :key="image.id">
            <div class="col-md-2 mb-4">
              <img :src="image" :alt="event.name">
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  name: 'EventSingle',
  data () {
    return {
      event: {},
      events: [
        {
          id: 1,
          name: 'Charity Ball',
          category: 'Fundraising',
          description: 'Spend an elegant night of dinner and dancing with us as we raise money for our new rescue farm.',
          featuredImage: 'https://placekitten.com/500/500',
          images: [
            'https://placekitten.com/500/500',
            'https://placekitten.com/500/500',
            'https://placekitten.com/500/500',
          ],
          location: '1234 Fancy Ave',
          date: '12-25-2019',
          time: '11:30'
        },
        {
          id: 2,
          name: 'Rescue Center Goods Drive',
          category: 'Adoptions',
          description: 'Come to our donation drive to help us replenish our stock of pet food, toys, bedding, etc. We will have live bands, games, food trucks, and much more.',
          featuredImage: 'https://placekitten.com/500/500',
          images: [
            'https://placekitten.com/500/500'
          ],
          location: '1234 Dog Alley',
          date: '11-21-2019',
          time: '12:00'
        }
      ]
    }  
  },
  created() {
    const ID = Number(this.$route.params.id);
    const events = this.events.find(event => event.id === ID);
    this.event = events;
  }
}
</script>

<style lang="scss" scoped>
  .event-single {
    text-align: left;
    margin-top: 30px;
  }
  .hero-head {
      background-color: #42b983;
        margin-bottom: 70px;
  }
  .event-images {
    margin-top: 50px;
  }
  .description {
    margin-bottom: 30px;
  }
</style>
