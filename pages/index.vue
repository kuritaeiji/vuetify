<template>
  <div class="home">
    <h1 class="text-subtitle-1 grey--text">
      Dashboard
    </h1>

    <v-container class="my-5">
      <v-row no-gutters class="mb-4">
        <v-tooltip top>
          <template #activator="{ on, attrs }">
            <v-btn
              small
              text
              color="grey"
              v-bind="attrs"
              v-on="on"
              @click="sortBy('title')"
            >
              <v-icon small left>
                mdi-file
              </v-icon>
              <span class="text-lowercase text-caption">by project name</span>
            </v-btn>
          </template>
          <span>sort projects by project name</span>
        </v-tooltip>

        <v-tooltip top>
          <template #activator="{ on, attrs }">
            <v-btn
              small
              text
              color="grey"
              v-bind="attrs"
              v-on="on"
              @click="sortBy('person')"
            >
              <v-icon left small>
                mdi-account
              </v-icon>
              <span class="text-lowercase">by person</span>
            </v-btn>
          </template>
          <span>sort projects by person</span>
        </v-tooltip>
      </v-row>

      <template v-for="project of projects">
        <v-card :key="project.title" flat :class="`py-3 project ${project.status}`">
          <v-row no-gutters>
            <v-col cols="12" md="6" class="px-3">
              <div class="text-caption grey--text">
                Project title
              </div>
              <div>
                {{ project.title }}
              </div>
            </v-col>
            <v-col cols="6" sm="4" md="2" class="px-3">
              <div class="text-caption grey--text">
                Person
              </div>
              <div>
                {{ project.person }}
              </div>
            </v-col>
            <v-col cols="6" sm="4" md="2" class="px-3">
              <div class="text-caption grey--text">
                Due By
              </div>
              <div>
                {{ project.due }}
              </div>
            </v-col>
            <v-col cols="6" sm="4" md="2" class="px-3">
              <div class="center">
                <v-chip small :class="`${project.status} white--text`">
                  {{ project.status }}
                </v-chip>
              </div>
            </v-col>
          </v-row>
        </v-card>
        <v-divider :key="project.title" />
      </template>
    </v-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      projects: [
        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' },
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!' }
      ]
    }
  },
  methods: {
    sortBy (prop) {
      this.projects.sort((a, b) => a[prop] > b[prop] ? 1 : -1)
    }
  }
}
</script>

<style scoped>
.project.ongoing {
  border-left: 4px solid orange;
}
.project.complete {
  border-left: 4px solid #3cd1c2;
}
.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.ongoing {
  background-color: orange;
}
.v-chip.complete {
  background-color: #3cd1c2;
}
.v-chip.overdue {
  background-color: tomato;
}
</style>
