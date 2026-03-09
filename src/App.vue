<template>
  <div class="app">
    <SchoolsAndDistrictsPage v-if="showSchoolsPage" />
    <template v-else>
    <div class="main-grid">
      <div class="left-column">
        <!-- 1. Ms. Elizabeth's impact -->
        <section class="left-section section-beige">
          <h2 class="section-title" v-html="'Ms. Elizabeth\'s <span class=\'section-title-highlight\'>impact</span> at <span class=\'section-title-highlight\'>Oakland Middle School</span>, <span class=\'section-title-highlight\'>Texas</span>'"></h2>
          <div class="section-inner">
            <ImpactStory ref="impactStoryRef" />
          </div>
        </section>
        <!-- 2. Partnership: dark purple, form + resources -->
        <section class="left-section section-partnership">
          <div class="partnership-wrap">
            <div class="partnership-grid">
              <div class="partnership-left">
                <h2 class="partnership-heading">
                  Wayground is excited to partner with <span class="partnership-heading-school">Oakland Middle School</span>
                </h2>
                <p class="partnership-sub">Recommend Wayground to your Leadership!</p>
                <form class="partnership-form" @submit.prevent="submitPartnershipForm">
                  <div class="partnership-field">
                    <label class="partnership-label">Email</label>
                    <input
                      v-model="partnershipName"
                      type="text"
                      class="partnership-input"
                      placeholder="Name of Coach / Principal / Other"
                      aria-label="Email"
                    />
                  </div>
                  <div class="partnership-field">
                    <label class="partnership-label">Email address</label>
                    <input
                      v-model="partnershipEmail"
                      type="email"
                      class="partnership-input"
                      placeholder="you@school.edu"
                      aria-label="Email address"
                    />
                  </div>
                  <div class="partnership-field">
                    <label class="partnership-label">Select role</label>
                    <select
                      v-model="partnershipRole"
                      class="partnership-select"
                      aria-label="Select role"
                    >
                      <option value="">Select role</option>
                      <option value="Instructional coach">Instructional coach</option>
                      <option value="Tech coach">Tech coach</option>
                      <option value="Principal">Principal</option>
                      <option value="Assistant principal">Assistant principal</option>
                      <option value="Head of department">Head of department</option>
                    </select>
                  </div>
                  <label class="partnership-checkbox-wrap">
                    <input v-model="shareCopyWithMe" type="checkbox" class="partnership-checkbox" aria-label="Share a copy with me" />
                    <span class="partnership-checkbox-label">Share a copy with me</span>
                  </label>
                  <button type="submit" class="partnership-submit">Submit</button>
                  <p class="partnership-submit-note">We'll reach out to your leadership to share how Wayground can further support Oakland Middle School.</p>
                </form>
              </div>
              <div class="partnership-right">
                <p class="partnership-resources-intro">We will share the below resources with your leadership for a quick look!</p>
                <div class="partnership-arrow" aria-hidden="true">
                  <svg viewBox="0 0 80 40" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 36 Q 20 8 76 4"/></svg>
                </div>
                <div class="partnership-resources">
                  <div class="partnership-resources-row">
                    <div class="partnership-resource partnership-resource--vertical">
                      <img src="/consolidate-your-tech-vertical.png" alt="Consolidate your tech" />
                    </div>
                    <div class="partnership-resource partnership-resource--vertical">
                      <img src="/deliver-instruction-vertical.png" alt="Deliver instruction for everyone & everything" />
                    </div>
                  </div>
                  <div class="partnership-resource partnership-resource--landscape">
                    <img src="/instructure-level4-landscape.png" alt="LearnPlatform by Instructure ESSA Level IV study" />
                  </div>
                </div>
              </div>
            </div>
            <footer class="partnership-footer">
              <span class="partnership-copy">© 2024 Wayground. All rights reserved.</span>
              <div class="partnership-links">
                <a href="#" class="partnership-link">Privacy Policy</a>
                <a href="#" class="partnership-link">Terms of Service</a>
                <a href="#" class="partnership-link">Accessibility</a>
              </div>
            </footer>
          </div>
        </section>
      </div>

      <!-- Right: fixed (sticky) -->
      <aside class="right-column">
        <div class="right-inner">
          <div class="right-column-card">
            <HeatMap />
          </div>
          <!-- Wayground in [State] – stats + schools near me -->
          <div class="right-column-card right-column-card--partners">
            <div class="partners-widget">
              <div class="partners-header">
                <span class="partners-brand">WAYGROUND</span>
                <span class="partners-region">in Texas</span>
                <div class="partners-map-icon" aria-hidden="true">
                  <svg viewBox="0 0 60 100" fill="currentColor" aria-hidden="true"><path d="M30 2 L55 25 L55 75 Q55 95 30 98 Q5 95 5 75 L5 25 Z"/></svg>
                </div>
              </div>
              <div class="partners-stat">
                <span class="partners-number">2,000</span>
                <span class="partners-label">schools and district partners</span>
              </div>
              <div class="partners-cta">
                <span class="partners-cta-icon" aria-hidden="true">
                  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
                </span>
                <p class="partners-question">What schools near me partner with Wayground?</p>
              </div>
              <div class="partners-school-cards" aria-label="Partner schools">
                <div class="partners-school-card">
                  <div class="partners-school-card-logo partners-school-card-logo--teal">OAKLAND MIDDLE SCHOOL</div>
                  <div class="partners-school-card-body">
                    <span class="partners-school-card-name">Oakland Middle School</span>
                    <span class="partners-school-card-tagline">Leading in academic excellence</span>
                  </div>
                </div>
                <div class="partners-school-card">
                  <div class="partners-school-card-logo partners-school-card-logo--image">
                    <span class="partners-school-card-logo-placeholder" aria-hidden="true">Lone Star</span>
                  </div>
                  <div class="partners-school-card-body">
                    <span class="partners-school-card-name">Lone Star Academy</span>
                    <span class="partners-school-card-tagline">Preparing the leaders of tomorrow</span>
                  </div>
                </div>
                <div class="partners-school-card">
                  <div class="partners-school-card-logo partners-school-card-logo--teal">HOUSTON HEIGHTS PREP</div>
                  <div class="partners-school-card-body">
                    <span class="partners-school-card-name">Houston Heights Prep</span>
                    <span class="partners-school-card-tagline">Innovative learning environments</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </aside>
    </div>

    <!-- Share impact modal collage of 6 slides + download -->
    <div v-if="showShareImpactModal" class="share-impact-backdrop" @click.self="closeShareImpactModal">
      <div class="share-impact-modal" role="dialog" aria-labelledby="share-impact-title" aria-modal="true" @click.stop>
        <button type="button" class="share-impact-close" aria-label="Close" @click="closeShareImpactModal">×</button>
        <h2 id="share-impact-title" class="share-impact-heading">Share your impact</h2>
        <p class="share-impact-sub">A collage of all 6 impact slides. Download to share.</p>
        <div v-if="generatingCollage" class="share-impact-generating">
          <span class="share-impact-spinner" aria-hidden="true" />
          <p>Creating your collage…</p>
        </div>
        <template v-else-if="slideImages.length === 6">
          <div class="share-impact-collage">
            <img
              v-for="(url, i) in slideImages"
              :key="i"
              class="share-impact-collage-img"
              :src="url"
              :alt="`Slide ${i + 1}`"
            />
          </div>
          <div class="share-impact-actions">
            <button type="button" class="share-impact-download" @click="downloadCollageImage">Download</button>
            <button type="button" class="share-impact-dismiss" @click="closeShareImpactModal">Close</button>
          </div>
        </template>
      </div>
    </div>
    </template>
  </div>
</template>

<script setup lang="ts">
import { ref, nextTick, onMounted, onUnmounted } from 'vue'
import HeatMap from './components/HeatMap.vue'
import ImpactStory from './components/ImpactStory.vue'
import SchoolsAndDistrictsPage from './views/SchoolsAndDistrictsPage.vue'

const showSchoolsPage = ref(window.location.hash === '#schools-and-districts')
function updateSchoolsPage() {
  showSchoolsPage.value = window.location.hash === '#schools-and-districts'
}
onMounted(() => {
  window.addEventListener('hashchange', updateSchoolsPage)
})
onUnmounted(() => {
  window.removeEventListener('hashchange', updateSchoolsPage)
})

const showShareModal = ref(false)
const showShareImpactModal = ref(false)
const impactStoryRef = ref<InstanceType<typeof ImpactStory> | null>(null)
const slideImages = ref<string[]>([])
const generatingCollage = ref(false)
const showThankYouModal = ref(false)
const adminName = ref('')
const adminEmail = ref('')
const adminRole = ref('')

const showSlideDeckModal = ref(false)
const showSlideDeckThankYouModal = ref(false)
const slideDeckEmail = ref('')

const partnershipName = ref('')
const partnershipEmail = ref('')
const partnershipRole = ref('')
const shareCopyWithMe = ref(true)
function submitPartnershipForm() {
  // Optional: send to API or show thank you
}

const confettiColors = ['#FF319F', '#FF6B9D', '#C7267A', '#FFB3D9', '#2d1b4e', '#F3EFDA']
const confettiPieces = Array.from({ length: 48 }, (_, i) => {
  const angle = (i / 48) * 2 * Math.PI + Math.random() * 0.5
  const dist = 55 + Math.random() * 50
  const dx = Math.cos(angle) * dist
  const dy = Math.sin(angle) * dist
  return {
    '--dx': `${dx}px`,
    '--dy': `${dy}px`,
    '--delay': `${(i * 0.015) + Math.random() * 0.08}s`,
    '--rot': `${Math.random() * 720 - 360}deg`,
    backgroundColor: confettiColors[i % confettiColors.length],
    width: `${5 + Math.random() * 6}px`,
    height: `${4 + Math.random() * 4}px`,
  }
})

function openShareModal() {
  showShareModal.value = true
}
function closeShareModal() {
  showShareModal.value = false
}
function submitShareModal() {
  closeShareModal()
  showThankYouModal.value = true
}
function closeThankYouModal() {
  showThankYouModal.value = false
}

function closeSlideDeckModal() {
  showSlideDeckModal.value = false
}
function submitSlideDeckModal() {
  showSlideDeckModal.value = false
  showSlideDeckThankYouModal.value = true
}
function closeSlideDeckThankYouModal() {
  showSlideDeckThankYouModal.value = false
}

function closeShareImpactModal() {
  showShareImpactModal.value = false
}

async function openShareImpactModal() {
  showShareImpactModal.value = true
  generatingCollage.value = true
  slideImages.value = []
  await nextTick()
  try {
    const urls = await impactStoryRef.value?.generateSlideImages?.() ?? []
    slideImages.value = urls
  } catch (e) {
    console.error('Generate slide images failed', e)
  } finally {
    generatingCollage.value = false
  }
}

function loadImage(src: string): Promise<HTMLImageElement> {
  return new Promise((resolve, reject) => {
    const img = new Image()
    img.crossOrigin = 'anonymous'
    img.onload = () => resolve(img)
    img.onerror = reject
    img.src = src
  })
}

async function downloadCollageImage() {
  const urls = slideImages.value
  if (urls.length !== 6) return
  try {
    const images = await Promise.all(urls.map(loadImage))
    const cols = 3
    const rows = 2
    const cellW = 400
    const cellH = 314
    const gap = 3
    const cw = cols * cellW + (cols - 1) * gap
    const ch = rows * cellH + (rows - 1) * gap
    const canvas = document.createElement('canvas')
    canvas.width = cw
    canvas.height = ch
    const ctx = canvas.getContext('2d')
    if (!ctx) return
    ctx.fillStyle = '#ffffff'
    ctx.fillRect(0, 0, cw, ch)
    for (let i = 0; i < 6; i++) {
      const img = images[i]
      const x = (i % cols) * (cellW + gap)
      const y = Math.floor(i / cols) * (cellH + gap)
      const scale = Math.min(cellW / img.width, cellH / img.height)
      const dw = img.width * scale
      const dh = img.height * scale
      const dx = x + (cellW - dw) / 2
      const dy = y + (cellH - dh) / 2
      ctx.drawImage(img, 0, 0, img.width, img.height, dx, dy, dw, dh)
    }
    const link = document.createElement('a')
    link.download = 'my-impact-collage.png'
    link.href = canvas.toDataURL('image/png')
    link.click()
  } catch (e) {
    console.error('Collage download failed', e)
  }
}
</script>

<style scoped>
.app {
  min-height: 100vh;
  background: #f5f5f0;
}

/* Grid: left ~2/3, right ~1/3. Right is sticky. Generous outer padding. */
.main-grid {
  --partnership-block-height: 740px;
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 1rem;
  max-width: none;
  width: 100%;
  margin: 0;
  padding: 0 0 0 2rem;
  align-items: stretch;
}

/* Left column: all scrollable content */
.left-column {
  min-width: 0;
}

/* Left sections: yellow/beige fills the column, minimal padding */
.left-section {
  padding: 0;
  background: #f8f6f2;
}
/* Same width and vertical alignment as .section-partnership: identical horizontal padding and shape */
.left-section.section-beige {
  background: #f8f6f2;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  width: 100%;
  min-width: 0;
  border-radius: 12px;
}
.left-section.section-white {
  background: #fff;
  border-top: 1px solid #e8e6e2;
}
/* Blank section: match Impact Story – yellow background, grid, same layout and white card size */
.section-blank {
  background: transparent;
  border-top: none;
  padding: 2.25rem 2.5rem;
}

/* Partnership section: dark purple; same left alignment as yellow (beige) section content */
/* Same horizontal padding and width as .section-beige so both containers match */
.section-partnership {
  background: #2d1b4e;
  padding: 3rem 2rem 3.5rem 3.25rem;
  border-radius: 12px;
  margin: 0;
  box-sizing: border-box;
  width: 100%;
  min-width: 0;
  height: var(--partnership-block-height);
  min-height: var(--partnership-block-height);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}
.partnership-wrap {
  max-width: 1000px;
  margin: 0;
  width: 100%;
  flex: 1;
  display: flex;
  flex-direction: column;
  min-height: 0;
  overflow: hidden;
}
.partnership-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
  margin-bottom: 2.5rem;
}
@media (max-width: 768px) {
  .partnership-grid {
    grid-template-columns: 1fr;
  }
}
.partnership-heading {
  font-size: 1.75rem;
  font-weight: 700;
  line-height: 1.4;
  margin: 0 0 0.75rem;
  color: #FF319F;
  font-family: inherit;
  text-align: left;
}
.partnership-heading-school {
  font-size: 1.95rem;
  font-weight: 800;
}
.partnership-sub {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.85);
  margin: 0 0 1.75rem;
  line-height: 1.5;
}
.partnership-form {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}
.partnership-label {
  display: block;
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 0.35rem;
}
.partnership-input {
  width: 100%;
  max-width: 320px;
  padding: 0.65rem 0.9rem;
  font-size: 1rem;
  border: 1px solid rgba(0, 0, 0, 0.12);
  border-radius: 8px;
  background: #F3EFDA;
  color: #1a1a2e;
  box-sizing: border-box;
}
.partnership-input::placeholder {
  color: #6B7C93;
}
.partnership-select {
  width: 100%;
  max-width: 320px;
  padding: 0.6rem 0.75rem;
  font-size: 1rem;
  font-family: inherit;
  border: 1px solid rgba(0, 0, 0, 0.12);
  border-radius: 8px;
  background: #F3EFDA;
  color: #1a1a2e;
  box-sizing: border-box;
  cursor: pointer;
}
.partnership-select:focus {
  outline: none;
  border-color: rgba(139, 92, 246, 0.4);
}
.partnership-checkbox-wrap {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  margin-top: 0.25rem;
}
.partnership-checkbox {
  width: 1.1rem;
  height: 1.1rem;
  accent-color: #FF319F;
  cursor: pointer;
  flex-shrink: 0;
}
.partnership-checkbox-label {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.95);
  user-select: none;
}
.partnership-submit {
  align-self: flex-start;
  padding: 0.7rem 1.75rem;
  margin-top: 0.5rem;
  font-size: 1rem;
  font-weight: 600;
  color: #fff;
  background: #FF319F;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 0.25rem;
}
.partnership-submit:hover {
  background: #e02d8d;
}
.partnership-submit-note {
  font-size: 0.82rem;
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.45;
  margin: 0.75rem 0 0;
  max-width: 320px;
}
.partnership-right {
  position: relative;
  min-width: 0;
  padding-right: 0.5rem;
}
.partnership-resources-intro {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.75);
  margin: 0 0 0.5rem;
  position: relative;
  z-index: 2;
  min-width: 0;
  max-width: 100%;
  line-height: 1.4;
}
.partnership-arrow {
  position: absolute;
  left: 0;
  top: 1.5rem;
  width: 70px;
  height: 36px;
  color: #FF319F;
  opacity: 0.9;
  z-index: 1;
}
.partnership-arrow svg {
  width: 100%;
  height: 100%;
}
.partnership-resources {
  margin-top: 1.5rem;
  padding-left: 0.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 100%;
}
.partnership-resources-row {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  align-items: flex-start;
  flex-wrap: wrap;
}
.partnership-resource {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
  background: #fff;
}
.partnership-resource img {
  display: block;
  width: 100%;
  height: auto;
}
/* Vertical cards (Consolidate + Deliver instruction) – side by side */
.partnership-resource--vertical {
  max-width: 220px;
  flex-shrink: 0;
}
.partnership-resources-row .partnership-resource--vertical img {
  max-height: 420px;
  width: auto;
  max-width: 100%;
  object-fit: contain;
  object-position: top center;
}
/* Instructure Level 4 & Peer-Reviewed – landscape, big enough */
.partnership-resource--landscape img {
  max-height: 280px;
  object-fit: contain;
  object-position: center;
}
.partnership-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.75rem;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.15);
}
.partnership-copy {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.7);
}
.partnership-links {
  display: flex;
  gap: 1.25rem;
}
.partnership-link {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
}
.partnership-link:hover {
  color: #fff;
  text-decoration: underline;
}

.blank-impact-wrap {
  position: relative;
  width: 100%;
  height: 720px;
  background: #F3EFDA;
  border-radius: 12px;
  overflow: hidden;
}
.blank-grid-bg {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(30, 58, 95, 0.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(30, 58, 95, 0.06) 1px, transparent 1px);
  background-size: 24px 24px;
  pointer-events: none;
}
.blank-container {
  position: relative;
  z-index: 1;
  height: 100%;
  max-width: 880px;
  margin: 0 auto;
  padding: 2rem 1.75rem;
  display: flex;
  flex-direction: column;
  box-sizing: border-box;
}
.blank-progress {
  flex: 0 0 auto;
  height: 4px;
}
.blank-story {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  min-height: 0;
}
.blank-narrative {
  flex: 0 0 auto;
  text-align: center;
  padding: 0.5rem 1rem;
}
.blank-headline {
  font-size: 1.5rem;
  font-weight: 500;
  line-height: 1.35;
  margin: 0 0 0.5rem;
  color: #1E3A5F;
}
.blank-body {
  font-size: 1.05rem;
  color: #FF319F;
  font-weight: 500;
  margin: 0;
  line-height: 1.6;
}
.blank-body--small {
  font-size: 0.9rem;
}
.blank-slide-viewer {
  flex: 1;
  min-height: 380px;
  position: relative;
  display: flex;
  align-items: stretch;
  gap: 0.5rem;
  min-width: 0;
}
.blank-slide-nav {
  flex: 0 0 auto;
  width: 40px;
  align-self: center;
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(0, 0, 0, 0.08);
  border-radius: 50%;
  color: #1E3A5F;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.06);
  transition: background 0.2s, box-shadow 0.2s;
}
.blank-slide-nav:hover {
  background: rgba(255, 255, 255, 0.95);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}
.blank-slide-nav:active {
  background: rgba(255, 255, 255, 1);
}
.blank-space {
  flex: 1;
  min-height: 0;
  width: 100%;
  background-color: #fff;
  border-radius: 16px;
  box-shadow: 0 2px 20px rgba(30, 58, 95, 0.08);
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem;
  overflow: hidden;
}
.blank-space-inner {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 0;
}
.blank-space-img {
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
  object-fit: contain;
  object-position: center;
  display: block;
}
/* One-pager layout (second PD section): dark purple bg, white + pink headline, school image right */
.blank-space--one-pager {
  padding: 1.25rem 1.5rem;
  align-items: stretch;
  min-height: 0;
  overflow: auto;
  background: #2d1b4e;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
  background-size: 20px 20px;
  box-sizing: border-box;
}
.one-pager-white-box {
  width: 100%;
  max-width: 100%;
  background: #fff;
  border-radius: 14px;
  padding: 1.35rem 1.5rem;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.15);
  box-sizing: border-box;
  min-height: 0;
}
.one-pager-layout {
  display: flex;
  align-items: center;
  gap: 2rem;
  width: 100%;
  max-width: 100%;
  min-height: 0;
  min-width: 0;
}
.one-pager-layout--image-only {
  justify-content: flex-start;
}
.one-pager-title-wrap {
  flex: 1;
  min-width: 0;
  max-width: 100%;
}
.one-pager-title {
  font-size: 1.75rem;
  font-weight: 600;
  color: #fff;
  margin: 0;
  line-height: 1.4;
  font-family: inherit;
}
.one-pager-title .one-pager-highlight {
  color: #FF319F;
}
/* Flag: pole starts at bottom of box and runs up; flag at top; or use custom image */
.one-pager-flag-wrap {
  display: flex;
  align-items: flex-start;
  flex-shrink: 0;
  align-self: stretch;
  background: none;
  padding: 0;
  margin: 0;
}
.one-pager-flag-wrap--image {
  align-items: center;
  justify-content: center;
  min-width: 0;
  flex: 1 1 auto;
}
.one-pager-section-image {
  max-width: 90%;
  max-height: 260px;
  width: auto;
  height: auto;
  object-fit: contain;
  display: block;
  border-radius: 8px;
}

/* Inline form on the right of the one-pager section (inside white box) */
.one-pager-form-wrap {
  flex: 0 0 auto;
  width: 300px;
  max-width: 45%;
  min-width: 0;
  padding: 0 0 0 1.5rem;
  border-left: 1px solid #e2e8f0;
  margin-left: 0.5rem;
  box-sizing: border-box;
}
.one-pager-form-heading {
  font-size: 1.05rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0 0 1rem;
  line-height: 1.3;
}
.one-pager-field {
  margin-bottom: 0.9rem;
}
.one-pager-field:last-of-type {
  margin-bottom: 1rem;
}
.one-pager-label {
  display: block;
  font-size: 0.8rem;
  font-weight: 600;
  color: #334155;
  margin-bottom: 0.35rem;
}
.one-pager-input,
.one-pager-select {
  width: 100%;
  padding: 0.5rem 0.65rem;
  font-size: 0.9rem;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  background: #f8fafc;
  color: #1e293b;
  font-family: inherit;
  box-sizing: border-box;
}
.one-pager-input::placeholder {
  color: #94a3b8;
}
.one-pager-select {
  cursor: pointer;
  appearance: auto;
}
.one-pager-form-actions {
  margin-top: 0.25rem;
}
.one-pager-submit {
  width: 100%;
  padding: 0.65rem 1rem;
  font-size: 0.95rem;
  font-weight: 600;
  color: #fff;
  background: #FF319F;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.2s;
}
.one-pager-submit:hover {
  background: #e02d8d;
}
.one-pager-flag-pole {
  width: 5px;
  height: 100%;
  min-height: 180px;
  background: #1a1a1a;
  border-radius: 3px;
  flex-shrink: 0;
  box-shadow: 1px 0 3px rgba(0, 0, 0, 0.2);
}
.one-pager-flag {
  position: relative;
  flex: 0 0 auto;
  width: 235px;
  height: 150px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 0.55rem 0.75rem;
  background: #fff;
  color: #2d1b4e;
  font-size: 0.98rem;
  font-weight: 700;
  text-align: center;
  line-height: 1.3;
  letter-spacing: 0.02em;
  transform-origin: left center;
  animation: flag-wave 2.8s ease-in-out infinite;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
  border-radius: 0 6px 6px 0;
}
.one-pager-flag-pinata-wrap {
  position: absolute;
  top: 0.35rem;
  right: 0.45rem;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  overflow: hidden;
  clip-path: circle(50% at 55% 45%);
  pointer-events: none;
}
.one-pager-flag-pinata {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 28% 42%;
  display: block;
}
.one-pager-flag-line {
  display: block;
}
.one-pager-flag-x {
  display: block;
  margin: 0.15em 0;
  font-weight: 800;
  font-size: 1.1em;
}
@keyframes flag-wave {
  0%, 100% { transform: skewY(0deg) scaleX(1); }
  25% { transform: skewY(3deg) scaleX(1.02); }
  50% { transform: skewY(-2.5deg) scaleX(0.98); }
  75% { transform: skewY(2deg) scaleX(1.01); }
}
.blank-download-wrap {
  flex: 0 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 0.5rem;
  gap: 0.5rem;
}
.blank-download-note {
  font-size: 0.8rem;
  color: #6B7C93;
  margin: 1rem 0 0;
  line-height: 1.4;
}
.blank-download-link {
  color: #2563eb;
  text-decoration: underline;
  cursor: pointer;
}
.blank-download-link:hover {
  color: #1d4ed8;
}
.blank-download-btn {
  background: #FF319F;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.75rem 1.85rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.2s, transform 0.1s;
}
.blank-download-btn:hover {
  background: #e02d8d;
}
.blank-download-btn:active {
  transform: scale(0.98);
}
.blank-controls-spacer {
  flex: 0 0 auto;
  height: 52px;
}
/* Vertical gap between left sections: match right column (map card + gap) so purple boxes align */
.left-section + .left-section {
  margin-top: 1.25rem;
}
.section-inner {
  margin-top: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Right column: no background container (cards sit on page background) */
.right-column {
  margin-top: 0;
  padding-top: 1.5rem;
  background: transparent;
  min-width: 0;
  border-radius: 0;
  border: none;
  box-shadow: none;
  display: flex;
  flex-direction: column;
}
.right-inner {
  padding: 0 1.5rem 2.25rem;
  min-width: 0;
  box-sizing: border-box;
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}
.right-inner .section-title {
  margin-bottom: 1.25rem;
}
.right-column-card {
  margin-top: 0;
  flex: 0 0 auto;
  height: 600px;
  min-height: 400px;
  border-radius: 12px;
  overflow: hidden;
  background: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.06);
  padding: 1.5rem;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  width: 100%;
  border: none;
}
.right-column-card :deep(.heat-map-container) {
  height: 100%;
  width: 100%;
  max-width: 100%;
  min-width: 0;
  display: flex;
  flex-direction: column;
  min-height: 0;
}
.right-column-card :deep(.ticker-section) {
  flex-shrink: 0;
  padding: 0 0 0.75rem;
}
.right-column-card :deep(.map-wrapper) {
  flex: 1;
  min-height: 0;
  display: flex;
  flex-direction: column;
  width: 100%;
  margin: 0 auto;
}
.right-column-card :deep(.region-map) {
  flex: 1;
  min-height: 0;
  width: 100%;
  object-fit: contain;
}

.right-column-card:first-child {
  margin-top: 6rem;
}

/* Partners widget: same height as left */
.right-column-card--partners {
  flex: 0 0 auto;
  height: var(--partnership-block-height);
  min-height: var(--partnership-block-height);
  margin-top: 0;
  padding: 1rem 1.5rem 1.5rem;
  background: #4a2c6a;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  width: 100%;
  box-sizing: border-box;
  overflow: hidden;
}
.partners-widget {
  color: #fff;
  font-family: inherit;
  flex: 1;
  display: flex;
  flex-direction: column;
  min-height: 0;
  width: 100%;
  overflow-y: auto;
}
.partners-header {
  display: flex;
  align-items: baseline;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.35rem;
  margin-bottom: 0.75rem;
  position: relative;
}
.partners-brand {
  font-size: 1.5rem;
  font-weight: 700;
  color: #FF319F;
  letter-spacing: 0.02em;
}
.partners-region {
  font-size: 1.15rem;
  font-weight: 400;
  color: rgba(255, 255, 255, 0.95);
}
.partners-map-icon {
  position: absolute;
  top: -0.25rem;
  right: 0;
  width: 36px;
  height: 54px;
  color: #FF319F;
  opacity: 0.9;
}
.partners-map-icon svg {
  width: 100%;
  height: 100%;
}
.partners-stat {
  text-align: center;
  margin-bottom: 0.75rem;
}
.partners-number {
  display: block;
  font-size: 3.25rem;
  font-weight: 800;
  color: #f4a261;
  line-height: 1.1;
  letter-spacing: -0.02em;
}
.partners-label {
  display: block;
  font-size: 1.1rem;
  color: #f4a261;
  margin-top: 0.35rem;
  font-weight: 400;
}
.partners-cta {
  display: flex;
  align-items: flex-start;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
}
.partners-cta-icon {
  flex-shrink: 0;
  width: 26px;
  height: 26px;
  color: #f4a261;
  margin-top: 0.15rem;
}
.partners-cta-icon svg {
  width: 100%;
  height: 100%;
}
.partners-question {
  font-size: 1.15rem;
  color: #fff;
  margin: 0;
  line-height: 1.4;
  font-weight: 400;
}
.partners-school-cards {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  overflow-y: auto;
  min-height: 0;
  margin-top: 2.25rem;
}
.partners-school-card {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  background: rgba(0, 0, 0, 0.25);
  border-radius: 12px;
  padding: 0.65rem 0.75rem;
  min-height: 0;
}
.partners-school-card-logo {
  flex-shrink: 0;
  width: 56px;
  height: 56px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.55rem;
  font-weight: 700;
  color: #fff;
  text-align: center;
  line-height: 1.2;
  letter-spacing: 0.02em;
  padding: 0.25rem;
  box-sizing: border-box;
}
.partners-school-card-logo--teal {
  background: #0d9488;
}
.partners-school-card-logo--image {
  background: #1e3a5f;
}
.partners-school-card-logo-placeholder {
  font-size: 0.6rem;
  color: rgba(255, 255, 255, 0.8);
}
.partners-school-card-body {
  display: flex;
  flex-direction: column;
  gap: 0.15rem;
  min-width: 0;
}
.partners-school-card-name {
  font-size: 1rem;
  font-weight: 700;
  color: #fff;
  line-height: 1.25;
}
.partners-school-card-tagline {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.85);
  line-height: 1.3;
}

.section-title-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.25rem;
  flex-wrap: wrap;
}
.section-title-row .section-title {
  margin: 0;
  flex: 1;
  min-width: 0;
}
.share-impact-btn {
  flex-shrink: 0;
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  font-weight: 600;
  font-family: inherit;
  color: #1a1a2e;
  background: #fff;
  border: 2px solid #FF319F;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.2s, color 0.2s;
}
.share-impact-btn:hover {
  background: #fff5fb;
}
.section-title {
  font-size: 1.65rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0 0 2.25rem;
  letter-spacing: -0.02em;
}
/* White space above main impact heading */
.left-section.section-beige > .section-title {
  margin-top: 3.5rem;
}
.section-title :deep(.section-title-highlight) {
  color: #FF319F;
}

.left-section.section-leaders {
  position: relative;
}
.leaders-accent {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, transparent 0%, #fbbf24 50%, transparent 100%);
}

@media (max-width: 1024px) {
  .main-grid {
    grid-template-columns: 1fr;
    padding: 1.5rem 1.25rem;
    gap: 1.5rem;
  }
  .left-section {
    padding: 1.75rem 1.5rem;
  }
  .left-section + .left-section {
    margin-top: 1.75rem;
  }
  .right-column {
    position: static;
    max-height: none;
    border-top: 1px solid #e8e6e2;
  }
  .right-inner {
    padding: 1.75rem 1.5rem;
  }
}
</style>

<style>
.share-modal-backdrop {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  background: rgba(0, 0, 0, 0.2);
  backdrop-filter: blur(6px);
  z-index: 10;
}
.share-modal-backdrop--section {
  position: absolute;
  inset: 0;
  border-radius: 12px;
}
.share-modal {
  position: relative;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
  width: 100%;
  max-width: 560px;
  overflow: hidden;
}
.share-modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  z-index: 2;
  width: 32px;
  height: 32px;
  padding: 0;
  border: none;
  background: none;
  font-size: 1.5rem;
  line-height: 1;
  color: #64748b;
  cursor: pointer;
  border-radius: 6px;
  transition: color 0.2s, background 0.2s;
}
.share-modal-close:hover {
  color: #1a1a2e;
  background: #f1f5f9;
}
.share-modal-layout {
  display: flex;
  min-height: 320px;
}
.share-modal-left {
  flex: 0 0 42%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.75rem 1.25rem;
  background: #f8fafc;
  border-radius: 16px 0 0 16px;
}
.share-modal-left--preview {
  padding: 1rem;
}
.share-modal-slide-preview {
  width: 100%;
  height: 100%;
  min-height: 200px;
  max-height: 280px;
  object-fit: contain;
  border-radius: 10px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
}
/* Get the Slide Deck modal: larger modal, bigger email field, submit lower */
.share-modal--slide-deck {
  max-width: 640px;
}
.share-modal--slide-deck .share-modal-layout {
  min-height: 380px;
}
.share-modal--slide-deck .share-modal-right {
  padding: 2rem 2rem 1.5rem;
}
.share-modal--slide-deck .share-modal-input {
  padding: 0.75rem 1rem;
  font-size: 1.0625rem;
}
.share-modal--slide-deck .share-modal-actions {
  margin-top: 2rem;
}
.share-modal--slide-deck .share-modal-submit {
  padding: 0.65rem 1.5rem;
  font-size: 1rem;
}
.share-modal--slide-deck .share-modal-slide-preview {
  max-height: 320px;
}
.share-modal-right {
  flex: 1;
  padding: 1.75rem 1.75rem 1.5rem;
  min-width: 0;
}
.share-modal-heading {
  font-size: 1.2rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0 0 1.25rem;
  letter-spacing: -0.02em;
}
.share-modal-field {
  margin-bottom: 1rem;
}
.share-modal-label {
  display: block;
  font-size: 0.875rem;
  font-weight: 600;
  color: #334155;
  margin-bottom: 0.35rem;
}
.share-modal-select,
.share-modal-input {
  width: 100%;
  padding: 0.55rem 0.75rem;
  font-size: 0.9375rem;
  font-family: inherit;
  border: 1px solid #e2e8f0;
  border-radius: 8px;
  background: #fff;
  color: #1a1a2e;
  box-sizing: border-box;
}
.share-modal-input::placeholder {
  color: #94a3b8;
}
.share-modal-actions {
  margin-top: 1.35rem;
  display: flex;
  justify-content: center;
}
.share-modal-submit {
  background: #FF319F;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 0.5rem 1.25rem;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.2s, transform 0.1s;
}
.share-modal-submit:hover {
  background: #e02d8d;
}
.share-modal-submit:active {
  transform: scale(0.98);
}
/* Flag inside modal (scaled down) */
.share-modal-flag-wrap {
  display: flex;
  align-items: flex-start;
  flex-shrink: 0;
  background: none;
  padding: 0;
  margin: 0;
}
.share-modal-flag-pole {
  width: 4px;
  height: 120px;
  min-height: 100px;
  background: #1a1a1a;
  border-radius: 2px;
  flex-shrink: 0;
  box-shadow: 1px 0 2px rgba(0, 0, 0, 0.2);
}
.share-modal-flag {
  position: relative;
  flex: 0 0 auto;
  width: 140px;
  height: 88px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 0.4rem 0.5rem;
  background: #fff;
  color: #2d1b4e;
  font-size: 0.7rem;
  font-weight: 700;
  text-align: center;
  line-height: 1.25;
  letter-spacing: 0.02em;
  transform-origin: left center;
  animation: share-modal-flag-wave 2.8s ease-in-out infinite;
  box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.12);
  border-radius: 0 4px 4px 0;
}
.share-modal-flag-pinata-wrap {
  position: absolute;
  top: 0.2rem;
  right: 0.25rem;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  overflow: hidden;
  clip-path: circle(50% at 55% 45%);
  pointer-events: none;
}
.share-modal-flag-pinata {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 28% 42%;
  display: block;
}
.share-modal-flag-line {
  display: block;
}
.share-modal-flag-x {
  display: block;
  margin: 0.1em 0;
  font-weight: 800;
  font-size: 1em;
}
@keyframes share-modal-flag-wave {
  0%, 100% { transform: skewY(0deg) scaleX(1); }
  25% { transform: skewY(3deg) scaleX(1.02); }
  50% { transform: skewY(-2.5deg) scaleX(0.98); }
  75% { transform: skewY(2deg) scaleX(1.01); }
}

/* Thank you modal: header (icons + pink X) + body (title, sub, pink Close) + confetti */
.thankyou-modal {
  position: relative;
  background: #fff;
  border-radius: 14px;
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
  min-width: 280px;
  max-width: 360px;
  overflow: hidden;
}
.thankyou-confetti {
  position: absolute;
  inset: -20px;
  pointer-events: none;
  z-index: 0;
}
.thankyou-confetti-piece {
  position: absolute;
  left: 50%;
  top: 50%;
  margin-left: -5px;
  margin-top: -5px;
  border-radius: 1px;
  animation: thankyou-confetti-burst 1s ease-out forwards;
  animation-delay: var(--delay, 0s);
  opacity: 0;
}
@keyframes thankyou-confetti-burst {
  0% {
    opacity: 1;
    transform: translate(0, 0) rotate(0deg);
  }
  100% {
    opacity: 0.9;
    transform: translate(var(--dx), var(--dy)) rotate(var(--rot, 0deg));
  }
}
.thankyou-header {
  position: relative;
  z-index: 1;
  background: #f5f0e8;
  padding: 1.5rem 1.5rem 1.75rem;
  min-height: 72px;
}
.thankyou-close {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  width: 28px;
  height: 28px;
  padding: 0;
  border: none;
  background: none;
  font-size: 1.5rem;
  line-height: 1;
  color: #FF319F;
  cursor: pointer;
  border-radius: 6px;
  transition: color 0.2s, background 0.2s;
}
.thankyou-close:hover {
  color: #e02d8d;
  background: rgba(255, 49, 159, 0.08);
}
.thankyou-icon {
  position: absolute;
  font-size: 1.1rem;
  color: rgba(0, 0, 0, 0.12);
  pointer-events: none;
}
.thankyou-icon--1 { top: 1.25rem; left: 18%; }
.thankyou-icon--2 { top: 1.5rem; left: 42%; }
.thankyou-icon--3 { top: 1.1rem; right: 28%; }
.thankyou-icon--4 { top: 1.4rem; right: 14%; font-size: 1.4rem; }
.thankyou-body {
  position: relative;
  z-index: 1;
  background: #fff;
  padding: 1.5rem 1.75rem 1.75rem;
  text-align: center;
}
.thankyou-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2d1b4e;
  margin: 0 0 0.5rem;
}
.thankyou-sub {
  font-size: 0.9375rem;
  font-weight: 400;
  color: #4a5568;
  margin: 0 0 1.25rem;
  line-height: 1.45;
}
.thankyou-dismiss {
  background: #FF319F;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.55rem 1.5rem;
  font-size: 0.9375rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
  transition: background 0.2s;
}
.thankyou-dismiss:hover {
  background: #e02d8d;
}

/* Share impact modal */
.share-impact-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(6px);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 1.5rem;
}
.share-impact-modal {
  position: relative;
  background: #fff;
  border-radius: 16px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.2);
  max-width: 90vw;
  max-height: 90vh;
  overflow: auto;
  padding: 1.75rem 2rem 2rem;
}
.share-impact-close {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  width: 36px;
  height: 36px;
  padding: 0;
  border: none;
  background: none;
  font-size: 1.5rem;
  line-height: 1;
  color: #64748b;
  cursor: pointer;
  border-radius: 8px;
}
.share-impact-close:hover {
  color: #1a1a2e;
  background: #f1f5f9;
}
.share-impact-heading {
  font-size: 1.35rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0 0 0.35rem;
}
.share-impact-sub {
  font-size: 0.9rem;
  color: #64748b;
  margin: 0 0 1.25rem;
}
.share-impact-generating {
  min-height: 280px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  color: #64748b;
  font-size: 0.95rem;
}
.share-impact-spinner {
  width: 40px;
  height: 40px;
  border: 3px solid #e2e8f0;
  border-top-color: #FF319F;
  border-radius: 50%;
  animation: share-impact-spin 0.8s linear infinite;
}
@keyframes share-impact-spin {
  to { transform: rotate(360deg); }
}
.share-impact-collage {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 4px;
  width: 100%;
  max-width: 600px;
  aspect-ratio: 3 / 2;
  background: #1a1a2e;
  border-radius: 12px;
  overflow: hidden;
  padding: 4px;
}
.share-impact-collage-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  background: #fff;
}
.share-impact-actions {
  display: flex;
  gap: 0.75rem;
  margin-top: 1.25rem;
  justify-content: center;
  flex-wrap: wrap;
}
.share-impact-download {
  background: #FF319F;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 0.55rem 1.25rem;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
}
.share-impact-download:hover {
  background: #e02d8d;
}
.share-impact-dismiss {
  background: #f1f5f9;
  color: #334155;
  border: none;
  border-radius: 8px;
  padding: 0.55rem 1.25rem;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  font-family: inherit;
}
.share-impact-dismiss:hover {
  background: #e2e8f0;
}
</style>
