<script setup>
import { ref } from 'vue'
import Card from 'primevue/card'
import Button from 'primevue/button'
import Tag from 'primevue/tag'
import Divider from 'primevue/divider'

// Daughter's information
const daughterName = ref('My Beautiful Daughter')
const age = ref(5)
const birthDate = ref('March 3, 2021')
const hobbies = ref(['Drawing', 'Dancing', 'Playing with toys', 'Reading stories', 'Singing'])
const favoriteColors = ref(['Pink', 'Purple', 'Rainbow', 'Sparkly Gold'])
const funFacts = ref([
  'Loves unicorns and fairies',
  'Can count to 100',
  'Best friend is her teddy bear',
  'Favorite food is ice cream',
  'Wants to be a princess when she grows up'
])

const photoUrl = ref('https://github.com/user-attachments/assets/3d6084dc-c0c1-4730-82a3-42e5da2de7e0')

// Interactive elements
const hugCount = ref(0)
const starCount = ref(0)

const sendHug = () => {
  hugCount.value++
}

const addStar = () => {
  starCount.value++
}

// Color palette for cute design
const colors = {
  pink: '#ffb6c1',
  lavender: '#e6e6fa',
  mint: '#98ff98',
  peach: '#ffdab9',
  blue: '#add8e6',
  purple: '#dda0dd'
}
</script>

<template>
  <div class="app-container">
    <!-- Decorative header -->
    <header class="header">
      <div class="header-content">
        <h1 class="title">🌟 {{ daughterName }} 🌟</h1>
        <p class="subtitle">A little princess who brightens every day</p>
        <div class="decoration">
          <i class="pi pi-star-fill star-icon"></i>
          <i class="pi pi-heart-fill heart-icon"></i>
          <i class="pi pi-sparkle sparkle-icon"></i>
        </div>
      </div>
    </header>

    <main class="main-content">
      <div class="grid">
        <!-- Photo Section - Centerpiece -->
        <div class="col-12 lg:col-6">
          <Card class="photo-card">
            <template #content>
              <div class="photo-container">
                <div class="photo-frame">
                  <img :src="photoUrl" alt="My Beautiful Daughter" class="daughter-photo" />
                  <div class="frame-decoration">
                    <i class="pi pi-star frame-star star-1"></i>
                    <i class="pi pi-heart frame-heart heart-1"></i>
                    <i class="pi pi-star frame-star star-2"></i>
                    <i class="pi pi-heart frame-heart heart-2"></i>
                  </div>
                </div>
                <div class="photo-caption">
                  <h3><i class="pi pi-camera mr-2"></i>My Sunshine</h3>
                  <p>Always smiling, always beautiful</p>
                </div>
              </div>
            </template>
          </Card>

          <!-- Interactive buttons -->
          <div class="interactive-buttons mt-4">
            <Card>
              <template #content>
                <h3 class="mb-3">Send Love to {{ daughterName.split(' ')[daughterName.split(' ').length - 1] }}</h3>
                <div class="flex flex-wrap gap-3">
                  <Button
                    @click="sendHug"
                    icon="pi pi-heart"
                    label="Send a Hug"
                    severity="danger"
                    class="p-button-rounded p-button-lg"
                    :style="{ backgroundColor: colors.pink, borderColor: colors.pink }"
                  />
                  <Button
                    @click="addStar"
                    icon="pi pi-star"
                    label="Add a Star"
                    severity="warning"
                    class="p-button-rounded p-button-lg"
                    :style="{ backgroundColor: colors.peach, borderColor: colors.peach }"
                  />
                </div>
                <div class="mt-3 stats">
                  <p><i class="pi pi-heart mr-2" style="color: #ff6b8b"></i> Hugs sent: <strong>{{ hugCount }}</strong></p>
                  <p><i class="pi pi-star mr-2" style="color: #ffd700"></i> Stars collected: <strong>{{ starCount }}</strong></p>
                </div>
              </template>
            </Card>
          </div>
        </div>

        <!-- Information Section -->
        <div class="col-12 lg:col-6">
          <!-- About Card -->
          <Card class="mb-4">
            <template #title>
              <i class="pi pi-info-circle mr-2"></i> About Me
            </template>
            <template #content>
              <div class="about-grid">
                <div class="about-item">
                  <i class="pi pi-calendar about-icon"></i>
                  <div>
                    <h4>Age</h4>
                    <p class="about-value">{{ age }} years old</p>
                  </div>
                </div>
                <div class="about-item">
                  <i class="pi pi-gift about-icon"></i>
                  <div>
                    <h4>Birthday</h4>
                    <p class="about-value">{{ birthDate }}</p>
                  </div>
                </div>
                <div class="about-item">
                  <i class="pi pi-sun about-icon"></i>
                  <div>
                    <h4>Personality</h4>
                    <p class="about-value">Joyful & Curious</p>
                  </div>
                </div>
                <div class="about-item">
                  <i class="pi pi-moon about-icon"></i>
                  <div>
                    <h4>Dream</h4>
                    <p class="about-value">To be a Princess</p>
                  </div>
                </div>
              </div>
            </template>
          </Card>

          <!-- Hobbies Card -->
          <Card class="mb-4">
            <template #title>
              <i class="pi pi-palette mr-2"></i> My Hobbies & Interests
            </template>
            <template #content>
              <div class="tags-container">
                <Tag
                  v-for="(hobby, index) in hobbies"
                  :key="index"
                  :value="hobby"
                  severity="success"
                  class="mr-2 mb-2 p-tag-rounded"
                  :style="{ backgroundColor: colors.lavender, color: '#6b5b95' }"
                />
              </div>
            </template>
          </Card>

          <!-- Favorite Colors Card -->
          <Card class="mb-4">
            <template #title>
              <i class="pi pi-palette mr-2"></i> Favorite Colors
            </template>
            <template #content>
              <div class="colors-container">
                <div
                  v-for="(color, index) in favoriteColors"
                  :key="index"
                  class="color-item"
                  :style="{ backgroundColor: getColorValue(color) }"
                >
                  <span>{{ color }}</span>
                </div>
              </div>
            </template>
          </Card>

          <!-- Fun Facts Card -->
          <Card>
            <template #title>
              <i class="pi pi-lightbulb mr-2"></i> Fun Facts About Me
            </template>
            <template #content>
              <ul class="fun-facts">
                <li v-for="(fact, index) in funFacts" :key="index">
                  <i class="pi pi-check-circle mr-2" style="color: #4caf50"></i>
                  {{ fact }}
                </li>
              </ul>
            </template>
          </Card>
        </div>
      </div>

      <!-- Footer -->
      <footer class="footer">
        <Divider />
        <p class="footer-text">
          Made with <i class="pi pi-heart" style="color: #ff6b8b"></i> by Dad
          | <i class="pi pi-star" style="color: #ffd700"></i>
          Every day with you is magical <i class="pi pi-magic" style="color: #9c27b0"></i>
        </p>
      </footer>
    </main>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #f5f7fa 0%, #fce4ec 100%);
  font-family: 'Nunito', 'Comic Neue', sans-serif;
}

.header {
  background: linear-gradient(90deg, #ffb6c1 0%, #e6e6fa 100%);
  padding: 2rem 1rem;
  text-align: center;
  border-bottom-left-radius: 30px;
  border-bottom-right-radius: 30px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
}

.header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%23ffffff' fill-opacity='0.1' fill-rule='evenodd'/%3E%3C/svg%3E");
  opacity: 0.3;
}

.title {
  font-size: 3rem;
  font-weight: 800;
  color: #6b5b95;
  margin-bottom: 0.5rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
}

.subtitle {
  font-size: 1.5rem;
  color: #9c89b8;
  margin-bottom: 1.5rem;
  font-family: 'Comic Neue', cursive;
}

.decoration {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 1rem;
}

.star-icon, .heart-icon, .sparkle-icon {
  font-size: 2rem;
  animation: float 3s ease-in-out infinite;
}

.star-icon { color: #ffd700; animation-delay: 0s; }
.heart-icon { color: #ff6b8b; animation-delay: 0.5s; }
.sparkle-icon { color: #9c27b0; animation-delay: 1s; }

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.main-content {
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.photo-card {
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}

.photo-container {
  text-align: center;
}

.photo-frame {
  position: relative;
  display: inline-block;
  margin-bottom: 1rem;
}

.daughter-photo {
  width: 100%;
  max-width: 400px;
  height: auto;
  border-radius: 15px;
  border: 10px solid white;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.frame-decoration {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.frame-star, .frame-heart {
  position: absolute;
  font-size: 1.5rem;
  animation: spin 4s linear infinite;
}

.star-1 { top: 10px; left: 10px; color: #ffd700; }
.heart-1 { top: 10px; right: 10px; color: #ff6b8b; }
.star-2 { bottom: 10px; left: 10px; color: #ffd700; animation-delay: 2s; }
.heart-2 { bottom: 10px; right: 10px; color: #ff6b8b; animation-delay: 2s; }

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.photo-caption {
  margin-top: 1rem;
}

.photo-caption h3 {
  color: #6b5b95;
  font-size: 1.8rem;
  margin-bottom: 0.5rem;
}

.photo-caption p {
  color: #9c89b8;
  font-style: italic;
}

.interactive-buttons .p-card {
  border-radius: 15px;
  background: linear-gradient(135deg, #ffffff 0%, #f8f8ff 100%);
}

.stats {
  font-size: 1.1rem;
  color: #6b5b95;
}

.stats strong {
  color: #9c27b0;
}

.about-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1rem;
}

.about-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.5rem;
  border-radius: 10px;
  background-color: rgba(255, 255, 255, 0.7);
}

.about-icon {
  font-size: 1.5rem;
  color: #9c89b8;
}

.about-item h4 {
  margin: 0;
  font-size: 0.9rem;
  color: #888;
}

.about-value {
  margin: 0;
  font-weight: 700;
  color: #6b5b95;
}

.tags-container {
  display: flex;
  flex-wrap: wrap;
}

.colors-container {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.color-item {
  padding: 0.5rem 1rem;
  border-radius: 20px;
  color: white;
  font-weight: 600;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
  min-width: 100px;
  text-align: center;
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
}

.fun-facts {
  list-style: none;
  padding: 0;
}

.fun-facts li {
  padding: 0.5rem 0;
  color: #555;
  font-size: 1.1rem;
}

.footer {
  margin-top: 3rem;
  text-align: center;
  padding: 1rem;
}

.footer-text {
  color: #9c89b8;
  font-size: 1.1rem;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .title {
    font-size: 2.2rem;
  }

  .subtitle {
    font-size: 1.2rem;
  }

  .about-grid {
    grid-template-columns: 1fr;
  }

  .daughter-photo {
    max-width: 300px;
  }
}
</style>

<script>
export default {
  methods: {
    getColorValue(colorName) {
      const colorMap = {
        'Pink': '#ffb6c1',
        'Purple': '#dda0dd',
        'Rainbow': 'linear-gradient(90deg, red, orange, yellow, green, blue, indigo, violet)',
        'Sparkly Gold': 'linear-gradient(45deg, #ffd700, #fffacd, #ffd700)'
      }
      return colorMap[colorName] || '#cccccc'
    }
  }
}
</script>