<template>
  <div>
    <h1 class="text-subtitle-1 grey--text">
      Team
    </h1>

    <v-container>
      <v-row>
        <v-col
          v-for="team of teams"
          :key="team.name"
          cols="12"
          sm="6"
          md="4"
          lg="3"
        >
          <v-card flat class="text-center">
            <div class="pt-4">
              <v-avatar size="100" class="grey lighten-2">
                <v-img :src="team.avatar" />
              </v-avatar>
            </div>

            <v-card-text>
              <div class="text-subtitle-1">
                {{ team.name }}
              </div>
              <div class="grey--text">
                {{ team.role }}
              </div>
            </v-card-text>

            <v-card-actions class="d-flex justify-center">
              <v-btn text color="grey">
                <v-icon left>
                  mdi-message
                </v-icon>
                <span>message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import img from '@/assets/a.jpg'
import avatar1 from '@/assets/avatar-1.png'
import avatar2 from '@/assets/avatar-2.png'
import avatar3 from '@/assets/avatar-3.png'
import avatar4 from '@/assets/avatar-4.png'
import avatar5 from '@/assets/avatar-5.png'

export default {
  data () {
    return {
      teams: [
        { name: 'The Net Ninja', role: 'Web developer', avatar: avatar1 },
        { name: 'Ryu', role: 'Graphic designer', avatar: avatar2 },
        { name: 'Chun Li', role: 'Web developer', avatar: avatar3 },
        { name: 'Gouken', role: 'Social media maverick', avatar: avatar4 },
        { name: 'Yoshi', role: 'Sales guru', avatar: avatar5 }
      ],
      img
    }
  }
}
</script>
