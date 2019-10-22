<template>
  <article>
    <div class="sm:flex md:flex-row-reverse xl:flex bg-gray-900"> <!-- md:flex-row-reverse -->
      <div class="px-2 
                  pb-2 mt-16
                  md:pt-2
                  sm:pt-6 
                  sm:px-2
                  md:pt-6
                  md:px-2
                  lg:pt-6
                  lg:px-2
                  max-w-full
                  sm:w-full
                  md:w-full
                  lg:max-w-full
                  lg:w-3/4"
      >
        <div class="push-down sm:flex
                    pt-1 sm:-mt-1 -mt-1 sm:pt-1 md:pt-1 lg:pt-1
                    md:flex-grow-0
                    xl:flex">
          <selectable-plan
            plan-name="Do the"
            plan-subtitle="fucking work"
            plan-gigs="1"
            plan-dollars="5"
            v-model="activePlan"
          ></selectable-plan>
          <selectable-plan
            plan-name="Growth"
            plan-subtitle="take advantage of it."
            plan-gigs="5"
            plan-dollars="10"
            v-model="activePlan"
          ></selectable-plan>
        </div>

      </div>
      <div class="hidden lg:block lg:w-1/4 xl:w-5/12 bg-cover" style="background-image: url('https://images.unsplash.com/photo-1554188248-986adbb73be4?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80')" title="cover">
      </div>
    </div>


    




      <div class="sm:flex md:flex xl:flex">
        <div class="w-full md:w-2/4 sm:w-full">
         
            <div class="antialiased pt-0 text-gray-900">
              <div class="flex justify-center">
                <PropertyCard :property="property"/>
              </div>
            </div>
            
        </div>
        <div class="hidden md:block md:w-1/2 lg:block lg:w-1/2 xl:w-1/2">
          
          <div class="antialiased pt-0 text-gray-900">
            <div class="flex justify-center">
              <PropertyCard :property="property"/>
            </div>
          </div>

        </div>
      </div>
      <!-- Hosed -->
      <!-- <div class="sm:flex md:flex xl:flex antialiased">
        <div class="max-w-full
                    sm:w-full
                    md:w-full
                    lg:max-w-full
                    lg:w-1/2"
        >
          <div class="push-down sm:flex
                      pt-1 sm:-mt-1 -mt-1 sm:pt-1 md:pt-1 lg:pt-1
                      md:flex-grow-0
                      xl:flex">
            <div class="antialiased pt-0 text-gray-900">
              <div class="flex justify-center">
                <PropertyCard :property="property"/>
              </div>
            </div>

          </div>
      </div>
      <div class="hidden md:block md:w-1/2 lg:block lg:w-1/2 xl:w-1/2">

        <div class="antialiased pt-0 text-gray-900">
          <div class="flex justify-center">
            <PropertyCard :property="property"/>
          </div>
        </div>

      </div>
    </div> -->


    <!-- <div>
      <div class="md:max-w-xl sm:max-w-xl lg:max-w-6xl mx-auto px-8 lg:px-12 py-8">
        <h2 class="text-xl text-gray-900">Popular destinations</h2>
        <p class="text-gray-600">A selection of great work-friendly cities with lots to see and explore.</p>
        <div class="flex flex-wrap -mx-4">
          <div class="mt-6 w-full px-4 lg:w-1/2 xl:w-1/3" v-for="destination in popularDestinations">
            <DestinationCard :destination="destination"/>
          </div>
        </div>
      </div>
    </div> -->

  </article>
</template>

<script>
import DestinationCard from '@theme/components/DestinationCard'
import SelectablePlan from '@theme/components/SelectablePlan'
import PropertyCard from '@theme/components/PropertyCard'

export default {
  name: 'app',
  components: {
    DestinationCard,
    SelectablePlan,
    PropertyCard
  },
  data: () => ({
    activePlan: '',
    property: {
      // imageUrl: 'https://images.unsplash.com/photo-1497366412874-3415097a27e7?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2100&q=80',
      imageUrl: 'https://images.unsplash.com/photo-1497366412874-3415097a27e7?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80',
      imageAlt: 'Rear view of modern home with pool',
      beds: 3,
      baths: 2,
      title: "Modern home in city center",
      priceInCents: 190000,
      formattedPrice: "$1,900.00",
      reviewCount: 34,
      rating: 4,
    },
    popularDestinations: [
    {
      city: 'Toronto',
      averagePrice: 120,
      propertyCount: 76,
      imageUrl: 'img/toronto.jpg',
      imageAlt: 'Toronto skyline',
    },
    {
      city: 'Malibu',
      averagePrice: 215,
      propertyCount: 43,
      imageUrl: '/img/malibu.jpg',
      imageAlt: 'Cliff in Malibu',
    },
    {
      city: 'Chicago',
      averagePrice: 130,
      propertyCount: 115,
      imageUrl: '/img/chicago.jpg',
      imageAlt: 'Chicago skyline',
    },
    {
      city: 'Seattle',
      averagePrice: 135,
      propertyCount: 63,
      imageUrl: '/img/seattle.jpg',
      imageAlt: 'Seattle skyline',
    },
    {
      city: 'Colorado',
      averagePrice: 85,
      propertyCount: 47,
      imageUrl: '/img/colorado.jpg',
      imageAlt: 'Lake in Colorado',
    },
    {
      city: 'Miami',
      averagePrice: 115,
      propertyCount: 86,
      imageUrl: '/img/miami.jpg',
      imageAlt: 'Beach in Miami',
    }]
  })
}
</script>

<style lang="stylus">
  @import '../styles/theme.styl';

  $sm-navbar-vertical-padding = 1.72rem

  @media (max-width: $MQMobile)
    .push-down
      padding-top $sm-navbar-vertical-padding
    
</style>