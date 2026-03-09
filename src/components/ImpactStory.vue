<template>
  <div class="impact-story-wrapper">
    <!-- Grid background -->
    <div class="grid-background" />

    <div class="container">
      <!-- Progress indicator -->
      <div
        class="progress-bar"
        role="progressbar"
        :aria-valuenow="currentState"
        aria-valuemin="1"
        :aria-valuemax="totalStates"
      >
        <div class="progress-fill" :style="{ width: progressWidth }" />
      </div>

      <!-- Main story area -->
      <main class="story" aria-live="polite" aria-atomic="true">
        <!-- Narrative text -->
        <header class="narrative">
          <h1 class="headline" :class="{ 'headline--slide3': currentState === 3 }" v-html="currentNarrative.headline" />
          <p v-if="currentNarrative.body" class="body-text" :class="{ 'body-text-hero': currentState === 1 || currentState === 2 || currentState === 3 || currentState === 4 || currentState === 5 || currentState === 6 }">{{ currentNarrative.body }}</p>
        </header>

        <!-- Journey visualization area: 3 pillars + statement -->
        <div ref="vizContainerRef" class="viz-container">
          <div class="viz-inner viz-inner--three-pillars">
            <!-- Page 1 only: original pillars -->
            <template v-if="currentState === 1">
              <div class="three-pillars">
                <div class="pillar pillar--daily">
                  <div class="pillar-visual pillar-visual--daily" aria-hidden="true">
                    <div class="daily-dots">
                      <span class="daily-dot" style="--i: 0" />
                      <span class="daily-dot" style="--i: 1" />
                      <span class="daily-dot" style="--i: 2" />
                      <span class="daily-dot" style="--i: 3" />
                      <span class="daily-dot" style="--i: 4" />
                    </div>
                    <svg class="pillar-icon pillar-icon--daily" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You enabled <span class="pillar-title-key">persistent practice</span></h3>
                </div>
                <div class="pillar pillar--achievement">
                  <div class="pillar-visual pillar-visual--achievement" aria-hidden="true">
                    <div class="achievement-bars">
                      <span class="achievement-bar" style="--i: 0; --h: 45%" />
                      <span class="achievement-bar" style="--i: 1; --h: 70%" />
                      <span class="achievement-bar" style="--i: 2; --h: 95%" />
                    </div>
                    <svg class="pillar-icon pillar-icon--achievement" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You accelerated <span class="pillar-title-key">student growth</span></h3>
                </div>
                <div class="pillar pillar--impact">
                  <div class="pillar-visual pillar-visual--impact" aria-hidden="true">
                    <span class="impact-pulse" />
                    <svg class="pillar-icon pillar-icon--impact" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="12" r="10"/><path d="M12 6v6l4 2"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You brought <span class="pillar-title-key">measurable progress</span></h3>
                </div>
              </div>
            </template>
            <!-- Page 2 only: You sparked engagement / drove active learning / inspired shared success -->
            <template v-else-if="currentState === 2">
              <div class="three-pillars">
                <div class="pillar pillar--daily">
                  <div class="pillar-visual pillar-visual--daily" aria-hidden="true">
                    <div class="engagement-sparkles">
                      <span class="engagement-sparkle" style="--i: 0" />
                      <span class="engagement-sparkle" style="--i: 1" />
                      <span class="engagement-sparkle" style="--i: 2" />
                      <span class="engagement-sparkle" style="--i: 3" />
                      <span class="engagement-sparkle" style="--i: 4" />
                    </div>
                    <svg class="pillar-icon pillar-icon--daily" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M12 3l1.5 4.5L18 9l-4.5 1.5L12 15l-1.5-4.5L6 9l4.5-1.5L12 3z"/><path d="M5 14l1-3 1 3 3-1-3-1-1-3-1 3z"/><path d="M19 10l.5-1.5L21 10l-1.5-.5L19 8l-.5 1.5L17 10l1.5.5L19 10z"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You sparked <span class="pillar-title-key">engagement.</span></h3>
                </div>
                <div class="pillar pillar--achievement">
                  <div class="pillar-visual pillar-visual--achievement" aria-hidden="true">
                    <div class="achievement-bars">
                      <span class="achievement-bar" style="--i: 0; --h: 45%" />
                      <span class="achievement-bar" style="--i: 1; --h: 70%" />
                      <span class="achievement-bar" style="--i: 2; --h: 95%" />
                    </div>
                    <svg class="pillar-icon pillar-icon--achievement" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2"/><path d="M12 7v6"/><path d="M8 10h8"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You drove <span class="pillar-title-key">active learning.</span></h3>
                </div>
                <div class="pillar pillar--impact">
                  <div class="pillar-visual pillar-visual--impact" aria-hidden="true">
                    <span class="success-pulse success-pulse--1" />
                    <span class="success-pulse success-pulse--2" />
                    <svg class="pillar-icon pillar-icon--impact" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You inspired <span class="pillar-title-key">shared success.</span></h3>
                </div>
              </div>
            </template>
            <!-- Page 3 only: insights into action / closed gaps / targeted small-group support -->
            <template v-else-if="currentState === 3">
              <div class="three-pillars">
                <div class="pillar pillar--insights">
                  <div class="pillar-visual pillar-visual--insights" aria-hidden="true">
                    <div class="insights-action-viz">
                      <span class="insights-line" />
                      <span class="insights-arrow" />
                    </div>
                    <svg class="pillar-icon pillar-icon--insights" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M3 3v18h18"/><path d="m19 9-5 5-4-4-3 3"/><path d="M15 3v6h6"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You turned <span class="pillar-title-key">insights into action</span></h3>
                </div>
                <div class="pillar pillar--gaps">
                  <div class="pillar-visual pillar-visual--gaps" aria-hidden="true">
                    <div class="gap-close-bars">
                      <span class="gap-bar gap-bar--short" />
                      <span class="gap-bar gap-bar--tall" />
                    </div>
                    <svg class="pillar-icon pillar-icon--gaps" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M12 20V4"/><path d="M6 20V12"/><path d="M18 20v-4"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You closed <span class="pillar-title-key">achievement gaps</span></h3>
                </div>
                <div class="pillar pillar--smallgroup">
                  <div class="pillar-visual pillar-visual--smallgroup" aria-hidden="true">
                    <div class="small-group-viz">
                      <span class="small-group-dot" style="--i: 0" />
                      <span class="small-group-dot" style="--i: 1" />
                      <span class="small-group-dot" style="--i: 2" />
                      <span class="small-group-ring" />
                    </div>
                    <svg class="pillar-icon pillar-icon--smallgroup" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M9 11a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/><path d="M15 11a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/><path d="M5 21v-2a4 4 0 0 1 4-4h2"/><path d="M19 21v-2a4 4 0 0 0-4-4h-2"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You targeted <span class="pillar-title-key">small-group support</span></h3>
                </div>
              </div>
            </template>
            <!-- Page 4 only: accommodations / access / inclusion -->
            <template v-else-if="currentState === 4">
              <div class="three-pillars">
                <div class="pillar pillar--access">
                  <div class="pillar-visual pillar-visual--access" aria-hidden="true">
                    <div class="access-expand-viz">
                      <span class="access-ring access-ring--1" />
                      <span class="access-ring access-ring--2" />
                      <span class="access-ring access-ring--3" />
                    </div>
                    <svg class="pillar-icon pillar-icon--access" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="12" r="10"/><path d="M12 8v8"/><path d="M8 12h8"/><path d="M12 4v2"/><path d="M12 18v2"/><path d="M4 12h2"/><path d="M18 12h2"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You expanded <span class="pillar-title-key">access for every learner</span></h3>
                </div>
                <div class="pillar pillar--support">
                  <div class="pillar-visual pillar-visual--support" aria-hidden="true">
                    <div class="support-moments-viz">
                      <span class="support-dot" style="--i: 0" />
                      <span class="support-dot" style="--i: 1" />
                      <span class="support-dot" style="--i: 2" />
                      <span class="support-dot" style="--i: 3" />
                    </div>
                    <svg class="pillar-icon pillar-icon--support" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You provided <span class="pillar-title-key">accessible support</span></h3>
                </div>
                <div class="pillar pillar--inclusive">
                  <div class="pillar-visual pillar-visual--inclusive" aria-hidden="true">
                    <div class="inclusive-viz">
                      <span class="inclusive-circle inclusive-circle--1" />
                      <span class="inclusive-circle inclusive-circle--2" />
                      <span class="inclusive-circle inclusive-circle--3" />
                    </div>
                    <svg class="pillar-icon pillar-icon--inclusive" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You built an <span class="pillar-title-key">inclusive classroom</span></h3>
                </div>
              </div>
            </template>
            <!-- Page 5 only: state standards / curriculum targets / test readiness -->
            <template v-else-if="currentState === 5">
              <div class="three-pillars">
                <div class="pillar pillar--standards">
                  <div class="pillar-visual pillar-visual--standards" aria-hidden="true">
                    <div class="standards-mirror-viz">
                      <span class="mirror-bar mirror-bar--top" />
                      <span class="mirror-bar mirror-bar--bottom" />
                    </div>
                    <svg class="pillar-icon pillar-icon--standards" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M4 8h16"/><path d="M4 16h16"/><path d="M6 12h12"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You mirrored <span class="pillar-title-key">state standards</span></h3>
                </div>
                <div class="pillar pillar--targets">
                  <div class="pillar-visual pillar-visual--targets" aria-hidden="true">
                    <div class="targets-viz">
                      <span class="target-ring target-ring--1" />
                      <span class="target-ring target-ring--2" />
                      <span class="target-ring target-ring--3" />
                      <span class="target-bullseye" />
                    </div>
                    <svg class="pillar-icon pillar-icon--targets" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="6"/><circle cx="12" cy="12" r="2"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You hit <span class="pillar-title-key">curriculum targets.</span></h3>
                </div>
                <div class="pillar pillar--readiness">
                  <div class="pillar-visual pillar-visual--readiness" aria-hidden="true">
                    <div class="readiness-viz">
                      <span class="readiness-check" style="--i: 0" />
                      <span class="readiness-check" style="--i: 1" />
                      <span class="readiness-check" style="--i: 2" />
                    </div>
                    <svg class="pillar-icon pillar-icon--readiness" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="M9 12l2 2 4-4"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You verified <span class="pillar-title-key">test readiness</span></h3>
                </div>
              </div>
            </template>
            <!-- Page 6 only: persistence / reattempts / outcomes -->
            <template v-else-if="currentState === 6">
              <div class="three-pillars">
                <div class="pillar pillar--persistence">
                  <div class="pillar-visual pillar-visual--persistence" aria-hidden="true">
                    <div class="persistence-viz">
                      <span class="persistence-line" />
                      <span class="persistence-dot" />
                    </div>
                    <svg class="pillar-icon pillar-icon--persistence" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M13 2L3 14h9l-1 8 10-12h-9l1-8z"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You powered <span class="pillar-title-key">persistence</span></h3>
                </div>
                <div class="pillar pillar--reattempts">
                  <div class="pillar-visual pillar-visual--reattempts" aria-hidden="true">
                    <div class="reattempts-viz">
                      <span class="reattempt-arrow reattempt-arrow--1" />
                      <span class="reattempt-arrow reattempt-arrow--2" />
                    </div>
                    <svg class="pillar-icon pillar-icon--reattempts" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M3 12a9 9 0 1 0 9-9 9.75 9.75 0 0 0-6.74 2.74L3 8"/><path d="M3 3v5h5"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You championed <span class="pillar-title-key">reattempts</span></h3>
                </div>
                <div class="pillar pillar--outcomes">
                  <div class="pillar-visual pillar-visual--outcomes" aria-hidden="true">
                    <div class="outcomes-viz">
                      <span class="outcome-bar" style="--h: 40%" />
                      <span class="outcome-bar" style="--h: 70%" />
                      <span class="outcome-bar outcome-bar--max" style="--h: 100%" />
                    </div>
                    <svg class="pillar-icon pillar-icon--outcomes" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
                      <path d="M3 3v18h18"/><path d="m19 9-5 5-4-4-3 3"/>
                    </svg>
                  </div>
                  <h3 class="pillar-title">You maximized <span class="pillar-title-key">outcomes</span></h3>
                </div>
              </div>
            </template>
            <p class="pillar-statement" v-html="currentState === 2 ? 'You\'ve <span class=\'pillar-statement-highlight\'>ignited</span> <span class=\'pillar-statement-highlight\'>12,400</span> moments of <span class=\'pillar-statement-highlight\'>engagement</span>, transforming your classroom into a hub of <span class=\'pillar-statement-highlight\'>active participation</span>.' : currentState === 3 ? 'You\'ve turned <span class=\'pillar-statement-highlight\'>student insights</span> into <span class=\'pillar-statement-highlight\'>action</span>, closing <span class=\'pillar-statement-highlight\'>achievement gaps</span> and driving <span class=\'pillar-statement-highlight\'>success for all</span>.' : currentState === 4 ? 'You\'ve transformed <span class=\'pillar-statement-highlight\'>accessible support</span> into <span class=\'pillar-statement-highlight\'>shared growth</span>, ensuring <span class=\'pillar-statement-highlight\'>broader representation</span> and <span class=\'pillar-statement-highlight\'>equal opportunity for all</span>.' : currentState === 5 ? 'You\'ve turned <span class=\'pillar-statement-highlight\'>targeted test prep</span> into <span class=\'pillar-statement-highlight\'>measurable success</span>, elevating every student to <span class=\'pillar-statement-highlight\'>peak test performance</span>.' : currentState === 6 ? 'You\'ve turned <span class=\'pillar-statement-highlight\'>core instructional goals</span> into <span class=\'pillar-statement-highlight\'>proven mastery</span>, ensuring every student achieves <span class=\'pillar-statement-highlight\'>peak performance</span>.' : 'You\'ve <span class=\'pillar-statement-highlight\'>bridged</span> the gap between <span class=\'pillar-statement-highlight\'>daily practice</span> and <span class=\'pillar-statement-highlight\'>student achievement</span>, driving <span class=\'pillar-statement-highlight\'>high-impact results</span> through <span class=\'pillar-statement-highlight\'>every lesson</span>.'"></p>
          </div>
          <!-- Legacy viz (hidden, kept for refs if needed) -->
          <div class="viz-inner viz-inner--legacy" :class="{ 'viz-inner--split': currentState !== 6 }" style="display: none;">
            <div class="viz-bubble-column">
              <canvas ref="particleCanvas" class="particle-canvas" />
              <!-- Curly arrows (slide 2+) – slide 1 uses right-column list instead -->
            <!-- Curly arrows (moved to right column bullets) -->
            <div class="bubble-arrows-wrap" v-show="false" aria-hidden="true">
              <div class="arrow-block arrow-tl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 42 Q 4 22 14 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,10 14,16 14,4" />
                </svg>
                <span class="bubble-label" style="--i: 0">Active & rigorous learning</span>
              </div>
              <div class="arrow-block arrow-tr">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 42 Q 46 22 36 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,10 36,16 36,4" />
                </svg>
                <span class="bubble-label" style="--i: 1">Active content mastery</span>
              </div>
              <div class="arrow-block arrow-bl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 8 Q 4 28 14 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,40 14,36 14,44" />
                </svg>
                <span class="bubble-label" style="--i: 2">High rigor</span>
              </div>
              <div class="arrow-block arrow-br">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 8 Q 46 28 36 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,40 36,36 36,44" />
                </svg>
                <span class="bubble-label" style="--i: 3">Equal participation</span>
              </div>
            </div>
            <!-- Data Mosaic / Bento grid (slide 3: Student growth) -->
            <div class="data-mosaic" v-show="currentState === 3" aria-hidden="true">
              <div class="bento-grid">
                <div class="bento-cell bento-cell--wide bento-cell--pattern bento-cell--dots" style="grid-column: 1 / span 2; grid-row: 1; --bento-i: 0;" />
                <div class="bento-cell bento-cell--icon bento-cell--book" style="grid-column: 3; grid-row: 1; --bento-i: 1;" aria-hidden="true">
                  <svg class="bento-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2"/><path d="M8 7h8"/><path d="M8 11h6"/></svg>
                </div>
                <div class="bento-cell bento-cell--pattern bento-cell--lines" style="grid-column: 4; grid-row: 1; --bento-i: 2;" />
                <div class="bento-cell bento-cell--tall bento-cell--icon bento-cell--check" style="grid-column: 1; grid-row: 2 / span 2; --bento-i: 3;" aria-hidden="true">
                  <svg class="bento-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>
                </div>
                <div class="bento-cell bento-cell--pattern bento-cell--grid" style="grid-column: 2; grid-row: 2; --bento-i: 4;" />
                <div class="bento-cell bento-cell--wide bento-cell--pattern bento-cell--gradient" style="grid-column: 3 / span 2; grid-row: 2; --bento-i: 5;" />
                <div class="bento-cell bento-cell--icon bento-cell--lightbulb" style="grid-column: 2; grid-row: 3; --bento-i: 6;" aria-hidden="true">
                  <svg class="bento-icon bento-icon--glow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M15 14c.2-1 .7-1.7 1.5-2.5 1-.9 1.5-2.2 1.5-3.5A6 6 0 0 0 6 8c0 1 .2 2.2 1.5 3.5.7.8 1.3 1.5 1.5 2.5"/><path d="M9 18h6"/><path d="M10 22h4"/></svg>
                </div>
                <div class="bento-cell bento-cell--pattern bento-cell--dots bento-cell--alt" style="grid-column: 3; grid-row: 3; --bento-i: 7;" />
                <div class="bento-cell bento-cell--pattern bento-cell--noise" style="grid-column: 4; grid-row: 3; --bento-i: 8;" />
              </div>
            </div>
            <div class="bubble-arrows-wrap" v-show="false" aria-hidden="true">
              <div class="arrow-block arrow-tl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 42 Q 4 22 14 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,10 14,16 14,4" />
                </svg>
                <span class="bubble-label" style="--i: 0">Achievement gap detection</span>
              </div>
              <div class="arrow-block arrow-tr">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 42 Q 46 22 36 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,10 36,16 36,4" />
                </svg>
                <span class="bubble-label" style="--i: 1">Targeted small-groups</span>
              </div>
              <div class="arrow-block arrow-bl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 8 Q 4 28 14 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,40 14,36 14,44" />
                </svg>
                <span class="bubble-label" style="--i: 2">Data-driven planning</span>
              </div>
              <div class="arrow-block arrow-br">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 8 Q 46 28 36 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,40 36,36 36,44" />
                </svg>
                <span class="bubble-label" style="--i: 3">Active enrichment paths</span>
              </div>
            </div>
            <div class="bubble-arrows-wrap" v-show="false" aria-hidden="true">
              <div class="arrow-block arrow-tl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 42 Q 4 22 14 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,10 14,16 14,4" />
                </svg>
                <span class="bubble-label" style="--i: 0">Increased learner participation</span>
              </div>
              <div class="arrow-block arrow-tr">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 42 Q 46 22 36 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,10 36,16 36,4" />
                </svg>
                <span class="bubble-label" style="--i: 1">Stronger student inclusion</span>
              </div>
              <div class="arrow-block arrow-bl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 8 Q 4 28 14 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,40 14,36 14,44" />
                </svg>
                <span class="bubble-label" style="--i: 2">Closing access gaps</span>
              </div>
              <div class="arrow-block arrow-br">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 8 Q 46 28 36 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,40 36,36 36,44" />
                </svg>
                <span class="bubble-label" style="--i: 3">Broader student representation</span>
              </div>
            </div>
            <div class="bubble-arrows-wrap" v-show="false" aria-hidden="true">
              <div class="arrow-block arrow-tl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 42 Q 4 22 14 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,10 14,16 14,4" />
                </svg>
                <span class="bubble-label" style="--i: 0">Proven test readiness</span>
              </div>
              <div class="arrow-block arrow-tr">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 42 Q 46 22 36 10" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,10 36,16 36,4" />
                </svg>
                <span class="bubble-label" style="--i: 1">High-rigor question sets</span>
              </div>
              <div class="arrow-block arrow-bl">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 2 8 Q 4 28 14 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="24,40 14,36 14,44" />
                </svg>
                <span class="bubble-label" style="--i: 2">Targeted exam practice</span>
              </div>
              <div class="arrow-block arrow-br">
                <svg class="curly-arrow" viewBox="0 0 50 50">
                  <path class="arrow-line" d="M 48 8 Q 46 28 36 40" fill="none" stroke-width="2.2" stroke-linecap="butt" stroke-linejoin="round"/>
                  <polygon class="arrow-head" points="26,40 36,36 36,44" />
                </svg>
                <span class="bubble-label" style="--i: 3">Deep content prep</span>
              </div>
            </div>
            <div class="stat-display" :class="{ visible: showStatDisplay }">
              <span class="stat-value">{{ currentNarrative.stat }}</span>
              <span class="stat-label">{{ currentNarrative.statLabel }}</span>
            </div>
            <div class="growth-display" :class="{ visible: showGrowthLabels }">
              <div class="growth-item before">
                <span class="growth-value">{{ beforeValue }}</span>
                <span class="growth-label-text">Before</span>
              </div>
              <div class="growth-arrow">
                <svg width="48" height="24" viewBox="0 0 48 24" fill="none">
                  <path d="M0 12H44M44 12L34 4M44 12L34 20" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
              <div class="growth-item after">
                <span class="growth-value">{{ afterValue }}</span>
                <span class="growth-label-text">After</span>
              </div>
            </div>
            <div class="viz-note" :class="{ visible: showVizNote }">
              <span class="viz-note-dot" :style="{ background: accentColor }" />
              <span>{{ vizNoteText }}</span>
            </div>
            <!-- Oakland Middle School feature cards (slide 6) -->
            <div class="oakland-slide" v-show="currentState === 6" aria-hidden="true">
              <div class="oakland-cards">
                <div class="oakland-card" style="--card-i: 0">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"/><path d="m3.27 6.96 12 13.01"/><path d="M12 20.01V12"/><path d="M20.73 6.96 9 19.97"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">Unlimited storage</h3>
                  <p class="oakland-card-line1">Securely create all school-wide materials.</p>
                  <p class="oakland-card-line2">Centralized repository for teaching assets.</p>
                </div>
                <div class="oakland-card" style="--card-i: 1">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"/><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">LMS Integration</h3>
                  <p class="oakland-card-line1">Automated gradebook sync for teachers.</p>
                  <p class="oakland-card-line2">Seamless workflow between existing systems.</p>
                </div>
                <div class="oakland-card" style="--card-i: 2">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M9 11l3 3L22 4"/><path d="M21 12v7a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">Premium question types</h3>
                  <p class="oakland-card-line1">Advanced formats for high-rigor prep.</p>
                  <p class="oakland-card-line2">Interactive tools for deeper assessment.</p>
                </div>
                <div class="oakland-card" style="--card-i: 3">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3v18h18"/><path d="m19 9-5 5-4-4-3 3"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">Common assessments</h3>
                  <p class="oakland-card-line1">Consistent benchmarks across all classrooms.</p>
                  <p class="oakland-card-line2">Unified measuring of grade-level progress.</p>
                </div>
                <div class="oakland-card" style="--card-i: 4">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><rect width="7" height="9" x="3" y="3" rx="1"/><rect width="7" height="5" x="14" y="3" rx="1"/><rect width="7" height="9" x="14" y="12" rx="1"/><rect width="7" height="5" x="3" y="16" rx="1"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">Admin dashboard</h3>
                  <p class="oakland-card-line1">High-level oversight of campus metrics.</p>
                  <p class="oakland-card-line2">Centralized management of student data.</p>
                </div>
                <div class="oakland-card" style="--card-i: 5">
                  <div class="oakland-card-icon" aria-hidden="true">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2"/><path d="M8 7h8"/><path d="M8 11h8"/><path d="M8 15h6"/></svg>
                  </div>
                  <h3 class="oakland-card-heading">Shared library</h3>
                  <p class="oakland-card-line1">Centralized resource hub</p>
                  <p class="oakland-card-line2">Unified content library</p>
                  <p class="oakland-card-line">Shared teaching assets</p>
                  <p class="oakland-card-line">District-wide collaboration</p>
                </div>
              </div>
            </div>
            </div>
            <div v-if="currentState !== 6" class="viz-impact-column" :key="currentState">
              <h2 class="viz-impact-heading viz-impact-heading--animate" v-html="impactColumnBySlide[currentState - 1].heading"></h2>
              <ul class="viz-impact-list viz-impact-list--animate">
                <li v-for="(item, i) in impactColumnBySlide[currentState - 1].bullets" :key="i">{{ item }}</li>
              </ul>
            </div>
          </div>
        </div>
      </main>

      <!-- Navigation: Back + Next at bottom -->
      <nav class="controls" aria-label="Story navigation">
        <button
          class="btn btn-back"
          aria-label="Previous section"
          :disabled="currentState === 1"
          @click="goBack"
        >
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none" aria-hidden="true">
            <path d="M12 15L7 10L12 5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Back
        </button>
        <button
          class="btn btn-next"
          aria-label="Next section"
          :disabled="currentState === totalStates"
          @click="goNext"
        >
          Next
          <svg width="20" height="20" viewBox="0 0 20 20" fill="none" aria-hidden="true">
            <path d="M8 5L13 10L8 15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </nav>

      <!-- Click hint (shown on intro) -->
      <div class="click-hint" :class="{ visible: currentState === 1 }" aria-hidden="true">
        Data reflected from your Wayground usage in the past 6 months. 💜
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted, nextTick } from 'vue';
import html2canvas from 'html2canvas';

interface Narrative {
  label: string;
  headline: string;
  body: string;
  stat?: string;
  statLabel?: string;
}

const narratives: Narrative[] = [
  {
    label: '',
    headline: 'You conducted <span class="highlight highlight--dot-glow">40</span> Classroom activities!',
    body: '',
    stat: '40',
    statLabel: 'Games Played',
  },
  {
    label: '',
    headline: 'Your students answered a total of <span class="highlight">12,400</span> Questions!',
    body: '',
    stat: '12,400',
    statLabel: 'Questions Answered',
  },
  {
    label: '',
    headline: '<span class="highlight highlight--dot-glow">15</span> data reports reviewed!',
    body: '',
    stat: '60%',
    statLabel: 'Growth',
  },
  {
    label: '',
    headline: '<span class="highlight">200</span> times you provided students with accessible support!',
    body: '',
    stat: '200',
    statLabel: 'Times accommodated',
  },
  {
    label: '',
    headline: '<span class="highlight">33</span> times, you specifically focused on State test prep!',
    body: '',
    stat: '4,800',
    statLabel: 'Aligned Questions',
  },
  {
    label: '',
    headline: '<span class="highlight">33</span> Times You championed Mastery!',
    body: '',
    stat: '',
    statLabel: '',
  },
];

// Right column (impact) content per slide: heading + bullets
const impactColumnBySlide: { heading: string; bullets: string[] }[] = [
  {
    heading: 'Here\'s how these <span class="highlight">resources</span> <span class="highlight">fueled</span> your <span class="highlight">success</span> and your <span class="highlight">classroom\'s</span>.',
    bullets: ['Seamless, ongoing student checks', 'Aligned to your instructional goals', 'Hours of prep time reclaimed', 'Daily planning made effortless'],
  },
  {
    heading: 'Here is how those <span class="highlight">questions</span> translated into <span class="highlight">student success</span>:',
    bullets: ['Active & rigorous learning', 'Active content mastery', 'High rigor', 'Equal participation'],
  },
  {
    heading: 'See how these <span class="highlight">insights</span> helped you <span class="highlight">take action</span> in the <span class="highlight">classroom</span>',
    bullets: ['Achievement gap detection', 'Targeted small-groups', 'Data-driven planning', 'Active enrichment paths'],
  },
  {
    heading: 'See how these <span class="highlight">accommodations</span> <span class="highlight">translated</span> into <span class="highlight">shared classroom growth</span>',
    bullets: ['Increased learner participation', 'Stronger student inclusion', 'Closing access gaps', 'Broader student representation'],
  },
  {
    heading: 'Serious State Test Prep',
    bullets: ['Proven test readiness', 'High-rigor question sets', 'Targeted exam practice', 'Deep content prep'],
  },
  {
    heading: 'Empowering Oakland Middle School',
    bullets: ['Unlimited storage', 'LMS Integration', 'Premium question types', 'Common assessments', 'Admin dashboard', 'Shared library'],
  },
];

const currentState = ref(1);
const totalStates = narratives.length;
const particleCanvas = ref<HTMLCanvasElement | null>(null);
const vizContainerRef = ref<HTMLElement | null>(null);
const isCapturingForShare = ref(false);

const accentColor = '#A3E5E0';
const showVizNote = ref(false); // Hidden on all slides
const showGrowthLabels = ref(false);
const vizNoteText = computed(() => {
  const narrative = narratives[currentState.value - 1];
  return narrative.statLabel ? `${narrative.stat} ${narrative.statLabel}` : 'Each dot represents a student';
});
const beforeValue = ref('30%');
const afterValue = ref('90%');

// Hide stat display on slides where bubbles represent the count (show during share capture)
const showStatDisplay = computed(() => {
  if (isCapturingForShare.value) {
    const n = narratives[currentState.value - 1];
    return Boolean(n?.stat);
  }
  const hiddenSlides = [1, 2, 3, 4, 5, 6];
  return !hiddenSlides.includes(currentState.value);
});

const progressWidth = computed(() => `${(currentState.value / totalStates) * 100}%`);

const currentNarrative = computed(() => narratives[currentState.value - 1]);

function goNext() {
  if (currentState.value < totalStates) {
    currentState.value++;
    updateVisualization();
  }
}

function goBack() {
  if (currentState.value > 1) {
    currentState.value--;
    updateVisualization();
  }
}

function updateVisualization() {
  // Hide viz-note on all slides
  showVizNote.value = false;
  // Show growth labels only on Student Growth slide (slide 3) - now handled in canvas
  showGrowthLabels.value = false; // Disabled - using canvas labels instead

  // Reset all animation timers to fix fast replay bug
  checklistStartTime = Date.now();
  lineGraphStartTime = Date.now();
  constellationStartTime = Date.now();
  dotsStartTime = Date.now();
  gridStartTime = Date.now();

  // Reinitialize after DOM updates so padding/layout is correct when returning to slide 1
  nextTick(() => {
    requestAnimationFrame(() => {
      initParticles();
    });
  });
}

async function generateSlideImages(): Promise<string[]> {
  const el = vizContainerRef.value;
  if (!el) return [];
  const savedState = currentState.value;
  const urls: string[] = [];
  isCapturingForShare.value = true;
  try {
    for (let i = 1; i <= totalStates; i++) {
      currentState.value = i;
      updateVisualization();
      await nextTick();
      await new Promise<void>((r) => requestAnimationFrame(() => r()));
      await new Promise((r) => setTimeout(r, 500));
      const sourceCanvas = el.querySelector('canvas');
      const canvasDataUrl = sourceCanvas ? sourceCanvas.toDataURL('image/png') : null;
      const opts: Parameters<typeof html2canvas>[1] = {
        scale: 2,
        useCORS: true,
        backgroundColor: '#ffffff',
        logging: false,
      };
      if (canvasDataUrl) {
        opts.onclone = (_doc, clone) => {
          const c = clone.querySelector('canvas');
          if (c) {
            const img = _doc.createElement('img');
            img.src = canvasDataUrl;
            img.setAttribute('style', 'position:absolute;inset:0;width:100%;height:100%;object-fit:contain;');
            c.parentNode?.insertBefore(img, c);
            c.remove();
          }
        };
      }
      const canvas = await html2canvas(el, opts);
      urls.push(canvas.toDataURL('image/png'));
    }
  } finally {
    isCapturingForShare.value = false;
    currentState.value = savedState;
    updateVisualization();
  }
  return urls;
}

defineExpose({ generateSlideImages });

// Particle animation
interface Particle {
  x: number;
  y: number;
  targetX: number;
  targetY: number;
  radius: number;
  color: string;
  velocity: { x: number; y: number };
  isStatic: boolean;
  // For orbital/fission animation
  angle?: number;
  orbitRadius?: number;
  orbitSpeed?: number;
  centerX?: number;
  centerY?: number;
  // For fission pulse effect
  baseRadius?: number;
  pulsePhase?: number;
  pulseSpeed?: number;
  pulseAmplitude?: number;
  // For checklist animation
  checked?: boolean;
  checkTime?: number; // When this particle should be checked
  index?: number;
  // For support network animation
  isStudent?: boolean;
  supported?: boolean;
  supportCount?: number;
  isSupport?: boolean;
  studentIndex?: number;
  startTime?: number;
  hasStarted?: boolean;
  lightUpTime?: number;
  // For validation wave animation
  validated?: boolean;
  validationTime?: number;
  row?: number;
  col?: number;
  // For neurons animation
  appeared?: boolean;
  appearTime?: number;
  // For grid (slide 1) pop-in animation
  gridAppearTime?: number;
}

// Global animation time for synchronized effects
let animationTime = 0;
let checklistStartTime = 0;
let lineGraphStartTime = 0;
let constellationStartTime = 0;
let dotsStartTime = 0;
let gridStartTime = 0;
const lineGraphDuration = 2000; // 2 seconds animation
const gridPopDuration = 120; // ms per dot for stagger

let particles: Particle[] = [];

// Store constellation connections
interface Connection {
  from: number;
  to: number;
}
let constellationConnections: Connection[] = [];
let animationId: number | null = null;

// Get particle count based on current slide
type LayoutType = 'grid' | 'random' | 'growth' | 'fission' | 'checklist' | 'linegraph' | 'bento' | 'constellation' | 'dots' | 'gravity' | 'validation' | 'support';

function getParticleConfig() {
  const configs: Record<number, { count: number; layout: LayoutType; isStatic: boolean }> = {
    1: { count: 40, layout: 'grid', isStatic: true },           // 40 games
    2: { count: 124, layout: 'checklist', isStatic: false },    // 12,400 questions - 124 circles (each = 100 questions)
    3: { count: 0, layout: 'bento', isStatic: true },           // Growth slide - Data Mosaic (bento grid)
    4: { count: 200, layout: 'dots', isStatic: false },        // 200 accommodations - animated dots
    5: { count: 80, layout: 'validation', isStatic: false }, // 4,800 aligned - validation wave animation
    6: { count: 0, layout: 'bento', isStatic: true }, // Oakland Middle School - feature cards (no canvas)
  };
  return configs[currentState.value] || { count: 40, layout: 'random', isStatic: false };
}

function initParticles() {
  if (!particleCanvas.value) return;

  const canvas = particleCanvas.value;
  const rect = canvas.getBoundingClientRect();
  canvas.width = rect.width * window.devicePixelRatio;
  canvas.height = rect.height * window.devicePixelRatio;

  const ctx = canvas.getContext('2d');
  if (!ctx) return;

  ctx.scale(window.devicePixelRatio, window.devicePixelRatio);

  createParticlesForCurrentSlide(rect.width, rect.height);
  drawParticles();
}

function createParticlesForCurrentSlide(width: number, height: number) {
  const config = getParticleConfig();
  const colors = ['#ECEB75', '#DCD2EF', '#A3E5E0', '#FFD8B2'];
  particles = [];

  if (config.layout === 'grid') {
    // Calculate grid dimensions
    const count = config.count;
    const cols = Math.ceil(Math.sqrt(count));
    const rows = Math.ceil(count / cols);
    
    // Calculate spacing - center the grid
    const bubbleRadius = 12;
    const spacing = bubbleRadius * 3;
    const gridWidth = (cols - 1) * spacing;
    const gridHeight = (rows - 1) * spacing;
    const startX = (width - gridWidth) / 2;
    const startY = (height - gridHeight) / 2;

    for (let i = 0; i < count; i++) {
      const col = i % cols;
      const row = Math.floor(i / cols);
      const x = startX + col * spacing;
      const y = startY + row * spacing;

      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: bubbleRadius,
        color: colors[i % colors.length],
        velocity: { x: 0, y: 0 },
        isStatic: config.isStatic,
        gridAppearTime: i * 45, // Staggered pop-in like questions answered section (ms delay)
      });
    }
  } else if (config.layout === 'bento') {
    // Data Mosaic (bento grid) - drawn as HTML overlay, no canvas particles
    particles = [];
  } else if (config.layout === 'checklist') {
    // Checklist layout - grid of circles that get checked off one by one
    const count = config.count;
    const cols = Math.ceil(Math.sqrt(count * 1.5)); // Slightly wider than tall
    const rows = Math.ceil(count / cols);
    
    // Calculate spacing - center the grid
    const bubbleRadius = 10;
    const spacing = bubbleRadius * 2.5;
    const gridWidth = (cols - 1) * spacing;
    const gridHeight = (rows - 1) * spacing;
    const startX = (width - gridWidth) / 2;
    const startY = (height - gridHeight) / 2;
    
    // Reset checklist start time
    checklistStartTime = Date.now();
    
    for (let i = 0; i < count; i++) {
      const col = i % cols;
      const row = Math.floor(i / cols);
      const x = startX + col * spacing;
      const y = startY + row * spacing;
      
      // Time when this particle should be checked (staggered quickly)
      const checkTime = i * 30; // 30ms between each check (fast!)
      
      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: bubbleRadius,
        color: '#E2E8F0', // Start with light gray (unchecked)
        velocity: { x: 0, y: 0 },
        isStatic: false,
        checked: false,
        checkTime,
        index: i,
      });
    }
  } else if (config.layout === 'dots') {
    // Dots layout - small dots in centre, inset to leave space for arrows/labels like other views
    const count = config.count;
    const cols = Math.ceil(Math.sqrt(count * 1.2));
    const rows = Math.ceil(count / cols);
    const dotRadius = 4;
    // Content box inset from edges (room for corner arrows and statements)
    const insetX = width * 0.14;
    const insetY = height * 0.14;
    const contentWidth = width - 2 * insetX;
    const contentHeight = height - 2 * insetY;
    const spacing = Math.min(
      contentWidth / Math.max(cols - 1, 1),
      contentHeight / Math.max(rows - 1, 1)
    );
    const gridWidth = (cols - 1) * spacing;
    const gridHeight = (rows - 1) * spacing;
    const startX = insetX + (contentWidth - gridWidth) / 2;
    const startY = insetY + (contentHeight - gridHeight) / 2;
    dotsStartTime = Date.now();
    for (let i = 0; i < count; i++) {
      const col = i % cols;
      const row = Math.floor(i / cols);
      const x = startX + col * spacing;
      const y = startY + row * spacing;
      const appearTime = i * 2;
      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: dotRadius,
        color: '#A3E5E0',
        velocity: { x: 0, y: 0 },
        isStatic: false,
        index: i,
        checkTime: appearTime,
        checked: false,
      });
    }
  } else if (config.layout === 'fission') {
    // Atomic fission layout - central nucleus with particles orbiting and pulsing outward
    const centerX = width / 2;
    const centerY = height / 2;
    const fissionColors = ['#ECEB75', '#DCD2EF', '#A3E5E0', '#FFD8B2'];
    
    // Clear constellation connections (not used here)
    constellationConnections = [];
    
    // Create central nucleus (larger particle)
    particles.push({
      x: centerX,
      y: centerY,
      targetX: centerX,
      targetY: centerY,
      radius: 24,
      color: '#A3E5E0',
      velocity: { x: 0, y: 0 },
      isStatic: true,
      baseRadius: 24,
      pulsePhase: 0,
      pulseSpeed: 0.02,
      pulseAmplitude: 3,
      centerX,
      centerY,
      angle: 0,
    });
    
    // Create orbiting rings of particles
    const rings = [
      { count: 6, radius: 50, speed: 0.015, size: 8 },
      { count: 10, radius: 90, speed: -0.01, size: 6 },
      { count: 14, radius: 130, speed: 0.008, size: 5 },
      { count: 18, radius: 170, speed: -0.005, size: 4 },
    ];
    
    rings.forEach((ring, ringIndex) => {
      for (let i = 0; i < ring.count; i++) {
        const angle = (i / ring.count) * Math.PI * 2;
        const x = centerX + Math.cos(angle) * ring.radius;
        const y = centerY + Math.sin(angle) * ring.radius;
        
        // Add some variation to orbit radius for organic feel
        const orbitVariation = ring.radius + (Math.random() - 0.5) * 15;
        
        particles.push({
          x,
          y,
          targetX: x,
          targetY: y,
          radius: ring.size + Math.random() * 2,
          color: fissionColors[(ringIndex + i) % fissionColors.length],
          velocity: { x: 0, y: 0 },
          isStatic: false,
          angle,
          orbitRadius: orbitVariation,
          orbitSpeed: ring.speed * (0.8 + Math.random() * 0.4),
          centerX,
          centerY,
          // Pulse effect - particles breathe in/out
          baseRadius: orbitVariation,
          pulsePhase: Math.random() * Math.PI * 2,
          pulseSpeed: 0.02 + Math.random() * 0.01,
          pulseAmplitude: 8 + Math.random() * 5,
        });
      }
    });
    
    // Add some scattered outer particles (ejected from fission)
    for (let i = 0; i < 12; i++) {
      const angle = Math.random() * Math.PI * 2;
      const distance = 200 + Math.random() * 60;
      const x = centerX + Math.cos(angle) * distance;
      const y = centerY + Math.sin(angle) * distance;
      
      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: 3 + Math.random() * 2,
        color: fissionColors[Math.floor(Math.random() * fissionColors.length)],
        velocity: { 
          x: Math.cos(angle) * 0.3,
          y: Math.sin(angle) * 0.3
        },
        isStatic: false,
        angle,
        orbitRadius: distance,
        orbitSpeed: 0.002 * (Math.random() > 0.5 ? 1 : -1),
        centerX,
        centerY,
      });
    }
  } else if (config.layout === 'constellation') {
    // Network constellation layout - nodes with connections, some going off edges
    const count = 8; // Fewer main nodes for less density
    // Use colors consistent with slide 1
    const constellationColors = ['#ECEB75', '#DCD2EF', '#A3E5E0', '#FFD8B2'];
    
    // Start animation timer
    constellationStartTime = Date.now();
    constellationConnections = [];
    
    // Create main nodes spread across the canvas
    const padding = 80;
    const usableWidth = width - padding * 2;
    const usableHeight = height - padding * 2;
    
    // Predefined positions for a nice network layout
    const positions = [
      { x: 0.2, y: 0.25 },
      { x: 0.5, y: 0.15 },
      { x: 0.8, y: 0.3 },
      { x: 0.15, y: 0.6 },
      { x: 0.45, y: 0.5 },
      { x: 0.75, y: 0.55 },
      { x: 0.3, y: 0.85 },
      { x: 0.65, y: 0.8 },
    ];
    
    // Create main visible nodes
    for (let i = 0; i < count; i++) {
      const pos = positions[i];
      const x = padding + pos.x * usableWidth + (Math.random() - 0.5) * 30;
      const y = padding + pos.y * usableHeight + (Math.random() - 0.5) * 30;
      
      // Time when this node should appear
      const appearTime = i * 250;
      
      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: 14 + Math.random() * 8,
        color: constellationColors[i % constellationColors.length],
        velocity: { x: 0, y: 0 },
        isStatic: false,
        index: i,
        checkTime: appearTime,
        checked: false,
      });
    }
    
    // Create edge nodes (invisible, just for line endpoints going off canvas)
    const edgeNodes = [
      { x: -20, y: height * 0.3 },      // Left edge
      { x: -20, y: height * 0.7 },      // Left edge
      { x: width + 20, y: height * 0.25 }, // Right edge
      { x: width + 20, y: height * 0.6 },  // Right edge
      { x: width * 0.3, y: -20 },       // Top edge
      { x: width * 0.7, y: -20 },       // Top edge
      { x: width * 0.4, y: height + 20 }, // Bottom edge
      { x: width * 0.8, y: height + 20 }, // Bottom edge
    ];
    
    for (let i = 0; i < edgeNodes.length; i++) {
      const edge = edgeNodes[i];
      particles.push({
        x: edge.x,
        y: edge.y,
        targetX: edge.x,
        targetY: edge.y,
        radius: 0, // Invisible
        color: 'transparent',
        velocity: { x: 0, y: 0 },
        isStatic: false,
        index: count + i,
        checkTime: 0, // Appear immediately
        checked: true, // Already appeared
      });
    }
    
    // Create connections between main nodes (sparse)
    const mainConnections = [
      [0, 1], [1, 2], [0, 3], [1, 4], [2, 5],
      [3, 4], [4, 5], [3, 6], [4, 7], [5, 7], [6, 7]
    ];
    
    mainConnections.forEach(([from, to]) => {
      constellationConnections.push({ from, to });
    });
    
    // Create connections to edge nodes (lines going off canvas)
    const edgeConnections = [
      [0, count + 0], // Node 0 to left edge
      [3, count + 1], // Node 3 to left edge
      [2, count + 2], // Node 2 to right edge
      [5, count + 3], // Node 5 to right edge
      [1, count + 4], // Node 1 to top edge
      [2, count + 5], // Node 2 to top edge
      [6, count + 6], // Node 6 to bottom edge
      [7, count + 7], // Node 7 to bottom edge
    ];
    
    edgeConnections.forEach(([from, to]) => {
      constellationConnections.push({ from, to });
    });
  } else if (config.layout === 'validation') {
    // Validation layout - grid of bubbles that get validated by a sweeping wave
    const count = config.count;
    const cols = Math.ceil(Math.sqrt(count * 1.5)); // Wider than tall
    const rows = Math.ceil(count / cols);

    const bubbleRadius = 10;
    const spacing = bubbleRadius * 2.8;
    const gridWidth = (cols - 1) * spacing;
    const gridHeight = (rows - 1) * spacing;
    const startX = (width - gridWidth) / 2;
    const startY = (height - gridHeight) / 2 + 30; // Offset down for badge

    for (let i = 0; i < count; i++) {
      const col = i % cols;
      const row = Math.floor(i / cols);
      const x = startX + col * spacing;
      const y = startY + row * spacing;

      // Calculate validation time based on row (wave sweeps down row by row)
      const validationDelay = row * 400; // 400ms per row

      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: bubbleRadius,
        color: colors[i % colors.length], // Final color
        velocity: { x: 0, y: 0 },
        isStatic: true,
        validated: false, // Start unvalidated
        validationTime: validationDelay,
        row, // Store row for wave effect
      });
    }
  } else {
    // Random layout with movement
    for (let i = 0; i < config.count; i++) {
      const x = 40 + Math.random() * (width - 80);
      const y = 40 + Math.random() * (height - 80);
      particles.push({
        x,
        y,
        targetX: x,
        targetY: y,
        radius: 6 + Math.random() * 6,
        color: colors[Math.floor(Math.random() * colors.length)],
        velocity: { x: (Math.random() - 0.5) * 0.5, y: (Math.random() - 0.5) * 0.5 },
        isStatic: config.isStatic,
      });
    }
  }
}

function drawParticles() {
  if (!particleCanvas.value) return;

  const canvas = particleCanvas.value;
  const ctx = canvas.getContext('2d');
  if (!ctx) return;

  const rect = canvas.getBoundingClientRect();

  ctx.clearRect(0, 0, rect.width, rect.height);
  
  // Increment global animation time
  animationTime += 0.016; // ~60fps
  
  // Calculate elapsed time for checklist animation
  const elapsedTime = Date.now() - checklistStartTime;
  const constellationElapsed = Date.now() - constellationStartTime;
  
  // Calculate elapsed time for dots animation
  const dotsElapsed = Date.now() - dotsStartTime;
  
  // Check if this is a line graph (slide 3) - detect by checking if particles have index and baseRadius but no checkTime
  const isLineGraph = particles.length > 0 && 
    particles[0].index !== undefined && 
    particles[0].baseRadius !== undefined && 
    particles[0].checkTime === undefined &&
    !particles[0].pulsePhase;
  
  // Check if this is a dots layout (slide 4) - many small dots with radius = 3
  const isDots = particles.length > 0 && 
    particles[0].checkTime !== undefined && 
    particles[0].radius >= 3 &&
    particles[0].radius <= 5;
  
  // Check if this is a constellation layout - has connections
  const isConstellation = constellationConnections.length > 0;
  
  // Check if this is a fission layout (slide 5) - first particle is nucleus at center
  const isFission = particles.length > 0 &&
    particles[0].radius === 24 &&
    particles[0].isStatic === true &&
    particles[0].pulsePhase !== undefined;

  // Check if this is a validation layout - particles with validated property
  const isValidation = particles.length > 0 &&
    particles[0].validated !== undefined &&
    particles[0].validationTime !== undefined;

  // Check if this is a gravity layout - particles not static, have targets, and no special properties
  const isGravity = particles.length > 0 &&
    particles[0].isStatic === false &&
    particles[0].checkTime === undefined &&
    particles[0].pulsePhase === undefined &&
    particles[0].angle === undefined &&
    particles[0].validated === undefined &&
    particles.length === 64;

  // Check if this is the grid layout (slide 1 - Games played) with pop-in animation
  const isGrid = particles.length === 40 &&
    particles[0].gridAppearTime !== undefined &&
    particles[0].isStatic === true;
  const gridElapsed = Date.now() - gridStartTime;

  if (isGrid && particles.length > 0) {
    // Grid dots with staggered pop-in animation (like questions answered section)
    particles.forEach((particle) => {
      const delay = particle.gridAppearTime ?? 0;
      const elapsed = Math.max(0, gridElapsed - delay);
      const progress = Math.min(elapsed / gridPopDuration, 1);
      const easeOutBack = 1 + 2.5 * Math.pow(progress - 1, 3) + 1.5 * Math.pow(progress - 1, 2);
      const scale = Math.max(0, Math.min(1, easeOutBack));

      if (scale <= 0) return;

      ctx.save();
      ctx.translate(particle.x, particle.y);
      ctx.scale(scale, scale);
      ctx.beginPath();
      ctx.arc(0, 0, particle.radius, 0, Math.PI * 2);
      ctx.fillStyle = particle.color;
      ctx.globalAlpha = 0.9;
      ctx.fill();
      ctx.globalAlpha = 1;
      ctx.restore();
    });
  } else if (isLineGraph && particles.length > 0) {
    // Draw line graph with animation
    const padding = { left: 60, right: 40, top: 40, bottom: 50 };
    const graphWidth = rect.width - padding.left - padding.right;
    const graphHeight = rect.height - padding.top - padding.bottom;
    
    // Calculate animation progress (0 to 1 over 2 seconds)
    const lineGraphElapsed = Date.now() - lineGraphStartTime;
    const progress = Math.min(lineGraphElapsed / lineGraphDuration, 1);
    // Use easeOutCubic for smooth animation
    const easedProgress = 1 - Math.pow(1 - progress, 3);
    
    // How many points to show based on progress
    const visiblePoints = Math.floor(easedProgress * (particles.length - 1)) + 1;
    // Partial progress to next point for smooth line drawing
    const partialProgress = (easedProgress * (particles.length - 1)) % 1;
    
    // Draw grid lines
    ctx.strokeStyle = 'rgba(107, 124, 147, 0.15)';
    ctx.lineWidth = 1;
    
    // Horizontal grid lines (every 20%)
    for (let i = 0; i <= 5; i++) {
      const y = padding.top + (i / 5) * graphHeight;
      ctx.beginPath();
      ctx.moveTo(padding.left, y);
      ctx.lineTo(padding.left + graphWidth, y);
      ctx.stroke();
    }
    
    // Draw Y-axis labels
    ctx.fillStyle = '#6B7C93';
    ctx.font = '12px system-ui, sans-serif';
    ctx.textAlign = 'right';
    ctx.textBaseline = 'middle';
    
    for (let i = 0; i <= 5; i++) {
      const percent = 100 - i * 20;
      const y = padding.top + (i / 5) * graphHeight;
      ctx.fillText(`${percent}%`, padding.left - 10, y);
    }
    
    // Draw axes
    ctx.strokeStyle = '#CBD5E1';
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(padding.left, padding.top);
    ctx.lineTo(padding.left, padding.top + graphHeight);
    ctx.lineTo(padding.left + graphWidth, padding.top + graphHeight);
    ctx.stroke();
    
    // Draw the animated line connecting points
    if (particles.length > 1 && visiblePoints >= 1) {
      // Create gradient for line
      const gradient = ctx.createLinearGradient(padding.left, 0, padding.left + graphWidth, 0);
      gradient.addColorStop(0, '#DCD2EF');
      gradient.addColorStop(0.3, '#A3E5E0');
      gradient.addColorStop(1, '#A3E5E0');
      
      ctx.strokeStyle = gradient;
      ctx.lineWidth = 3;
      ctx.lineCap = 'round';
      ctx.lineJoin = 'round';
      ctx.beginPath();
      ctx.moveTo(particles[0].x, particles[0].y);
      
      // Draw complete segments
      for (let i = 1; i < visiblePoints && i < particles.length; i++) {
        ctx.lineTo(particles[i].x, particles[i].y);
      }
      
      // Draw partial segment to next point if not complete
      if (visiblePoints < particles.length && partialProgress > 0) {
        const fromPoint = particles[visiblePoints - 1];
        const toPoint = particles[visiblePoints];
        const partialX = fromPoint.x + (toPoint.x - fromPoint.x) * partialProgress;
        const partialY = fromPoint.y + (toPoint.y - fromPoint.y) * partialProgress;
        ctx.lineTo(partialX, partialY);
      }
      ctx.stroke();
      
      // Fill area under the animated line
      ctx.beginPath();
      ctx.moveTo(particles[0].x, padding.top + graphHeight);
      ctx.lineTo(particles[0].x, particles[0].y);
      
      for (let i = 1; i < visiblePoints && i < particles.length; i++) {
        ctx.lineTo(particles[i].x, particles[i].y);
      }
      
      // Include partial segment in fill
      let lastX = particles[Math.min(visiblePoints - 1, particles.length - 1)].x;
      if (visiblePoints < particles.length && partialProgress > 0) {
        const fromPoint = particles[visiblePoints - 1];
        const toPoint = particles[visiblePoints];
        lastX = fromPoint.x + (toPoint.x - fromPoint.x) * partialProgress;
        const lastY = fromPoint.y + (toPoint.y - fromPoint.y) * partialProgress;
        ctx.lineTo(lastX, lastY);
      }
      
      ctx.lineTo(lastX, padding.top + graphHeight);
      ctx.closePath();
      
      const areaGradient = ctx.createLinearGradient(0, padding.top, 0, padding.top + graphHeight);
      areaGradient.addColorStop(0, 'rgba(0, 180, 160, 0.3)');
      areaGradient.addColorStop(1, 'rgba(0, 180, 160, 0.05)');
      ctx.fillStyle = areaGradient;
      ctx.fill();
    }
    
    // Draw visible points with animation
    for (let i = 0; i < visiblePoints && i < particles.length; i++) {
      const particle = particles[i];
      // Scale up animation for each point
      const pointDelay = i / particles.length;
      const pointProgress = Math.max(0, Math.min(1, (easedProgress - pointDelay) * 2));
      const scale = pointProgress;
      
      if (scale > 0) {
        ctx.beginPath();
        ctx.arc(particle.x, particle.y, particle.radius * scale, 0, Math.PI * 2);
        ctx.fillStyle = particle.color;
        ctx.fill();
        
        // Add white border to points
        ctx.strokeStyle = 'white';
        ctx.lineWidth = 2;
        ctx.stroke();
      }
    }
    
    // Draw 30% label on Y-axis (left side)
    ctx.font = 'bold 14px system-ui, sans-serif';
    ctx.textAlign = 'right';
    ctx.textBaseline = 'middle';
    const firstPoint = particles[0];
    ctx.fillStyle = '#6B7C93';
    ctx.fillText('30%', padding.left - 10, firstPoint.y);
    
    // Draw 90% label above the last point when animation is complete
    if (progress >= 1) {
      const lastPoint = particles[particles.length - 1];
      ctx.font = 'bold 16px system-ui, sans-serif';
      ctx.textAlign = 'center';
      ctx.fillStyle = '#1E3A5F';
      ctx.fillText('90%', lastPoint.x, lastPoint.y - 20);
    }

    // X-axis label
    ctx.fillStyle = '#6B7C93';
    ctx.font = '11px system-ui, sans-serif';
    ctx.textAlign = 'center';
    ctx.fillText('Time', padding.left + graphWidth / 2, rect.height - 15);
    
    // Y-axis label
    ctx.save();
    ctx.translate(15, padding.top + graphHeight / 2);
    ctx.rotate(-Math.PI / 2);
    ctx.fillText('Proficiency', 0, 0);
    ctx.restore();
    
  } else if (isDots && particles.length > 0) {
    // Dots layout - animated dots appearing one by one
    
    // Update and draw dots
    particles.forEach((particle) => {
      if (particle.checkTime !== undefined) {
        // Update appeared state based on elapsed time
        if (!particle.checked && dotsElapsed >= particle.checkTime) {
          particle.checked = true;
        }
      }
      
      // Only draw if appeared
      if (particle.checked) {
        ctx.beginPath();
        ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
        ctx.fillStyle = particle.color;
        ctx.globalAlpha = 0.85;
        ctx.fill();
        ctx.globalAlpha = 1;
      }
    });
    
  } else if (isFission && particles.length > 0) {
    // Atomic fission layout - nucleus with orbiting particles
    const centerX = rect.width / 2;
    const centerY = rect.height / 2;
    
    // Draw orbital paths (faint circles)
    ctx.strokeStyle = 'rgba(0, 180, 160, 0.1)';
    ctx.lineWidth = 1;
    const orbitRadii = [50, 90, 130, 170];
    orbitRadii.forEach(radius => {
      ctx.beginPath();
      ctx.arc(centerX, centerY, radius, 0, Math.PI * 2);
      ctx.stroke();
    });
    
    // Update and draw particles
    particles.forEach((particle, index) => {
      // Animate orbital particles
      if (!particle.isStatic && particle.angle !== undefined) {
        // Update angle for orbital motion
        if (particle.orbitSpeed !== undefined && particle.orbitSpeed !== 0) {
          particle.angle += particle.orbitSpeed;
        }
        
        // Calculate position - use pulse effect for breathing motion
        let currentRadius = particle.orbitRadius || 0;
        if (particle.pulsePhase !== undefined && particle.pulseAmplitude !== undefined) {
          const pulseOffset = Math.sin(animationTime * (particle.pulseSpeed || 0.02) * 60 + particle.pulsePhase) * particle.pulseAmplitude;
          currentRadius = (particle.baseRadius || particle.orbitRadius || 0) + pulseOffset;
        }
        
        particle.x = (particle.centerX || centerX) + Math.cos(particle.angle) * currentRadius;
        particle.y = (particle.centerY || centerY) + Math.sin(particle.angle) * currentRadius;
      }
      
      // Draw glow effect for nucleus
      if (index === 0) {
        // Central nucleus glow
        const nucleusGlow = ctx.createRadialGradient(
          particle.x, particle.y, 0,
          particle.x, particle.y, particle.radius * 3
        );
        nucleusGlow.addColorStop(0, 'rgba(0, 180, 160, 0.4)');
        nucleusGlow.addColorStop(0.5, 'rgba(0, 180, 160, 0.1)');
        nucleusGlow.addColorStop(1, 'transparent');
        
        ctx.beginPath();
        ctx.arc(particle.x, particle.y, particle.radius * 3, 0, Math.PI * 2);
        ctx.fillStyle = nucleusGlow;
        ctx.fill();
      }
      
      // Draw particle with glow
      const glow = ctx.createRadialGradient(
        particle.x, particle.y, 0,
        particle.x, particle.y, particle.radius * 1.5
      );
      glow.addColorStop(0, particle.color);
      glow.addColorStop(1, 'transparent');
      
      ctx.beginPath();
      ctx.arc(particle.x, particle.y, particle.radius * 1.5, 0, Math.PI * 2);
      ctx.fillStyle = glow;
      ctx.globalAlpha = 0.3;
      ctx.fill();
      ctx.globalAlpha = 1;
      
      // Draw main particle
      ctx.beginPath();
      ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
      ctx.fillStyle = particle.color;
      ctx.fill();
      
      // White border for larger particles
      if (particle.radius > 5) {
        ctx.strokeStyle = 'rgba(255, 255, 255, 0.6)';
        ctx.lineWidth = 1;
        ctx.stroke();
      }
    });
    
  } else if (isConstellation && particles.length > 0) {
    // Constellation layout - bubbles appearing and connecting with lines
    
    // Update appeared state for each particle
    particles.forEach((particle) => {
      if (particle.checkTime !== undefined) {
        if (!particle.checked && constellationElapsed >= particle.checkTime) {
          particle.checked = true;
        }
      }
    });
    
    // Draw connections first (behind nodes)
    ctx.lineWidth = 2;
    ctx.lineCap = 'round';
    
    constellationConnections.forEach((conn) => {
      const fromParticle = particles[conn.from];
      const toParticle = particles[conn.to];
      
      // Only draw connection if both nodes have appeared
      if (fromParticle?.checked && toParticle?.checked) {
        // Create gradient line between nodes
        const gradient = ctx.createLinearGradient(
          fromParticle.x, fromParticle.y,
          toParticle.x, toParticle.y
        );
        gradient.addColorStop(0, fromParticle.color);
        gradient.addColorStop(1, toParticle.color);
        
        ctx.strokeStyle = gradient;
        ctx.globalAlpha = 0.5;
        ctx.beginPath();
        ctx.moveTo(fromParticle.x, fromParticle.y);
        ctx.lineTo(toParticle.x, toParticle.y);
        ctx.stroke();
        ctx.globalAlpha = 1;
      }
    });
    
    // Draw nodes on top
    particles.forEach((particle) => {
      if (particle.checked) {
        // Draw glow effect
        const gradient = ctx.createRadialGradient(
          particle.x, particle.y, 0,
          particle.x, particle.y, particle.radius * 2
        );
        gradient.addColorStop(0, particle.color);
        gradient.addColorStop(1, 'transparent');
        
        ctx.beginPath();
        ctx.arc(particle.x, particle.y, particle.radius * 2, 0, Math.PI * 2);
        ctx.fillStyle = gradient;
        ctx.globalAlpha = 0.3;
        ctx.fill();
        ctx.globalAlpha = 1;
        
        // Draw main node
        ctx.beginPath();
        ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
        ctx.fillStyle = particle.color;
        ctx.fill();
        
        // White border
        ctx.strokeStyle = 'white';
        ctx.lineWidth = 2;
        ctx.stroke();
      }
    });

  } else if (isValidation && particles.length > 0) {
    // Validation Wave animation - bubbles transform from gray to color as wave sweeps down
    const elapsedTime = Date.now() - dotsStartTime;
    const waveY = 20 + (elapsedTime / 10); // Wave starts from top
    if (waveY < rect.height) {
      // Draw wave line
      ctx.strokeStyle = '#A3E5E0';
      ctx.lineWidth = 2;
      ctx.globalAlpha = 0.6;
      ctx.setLineDash([10, 5]);
      ctx.beginPath();
      ctx.moveTo(0, waveY);
      ctx.lineTo(rect.width, waveY);
      ctx.stroke();
      ctx.setLineDash([]);
      ctx.globalAlpha = 1;

      // Draw wave glow
      const waveGradient = ctx.createLinearGradient(0, waveY - 15, 0, waveY + 15);
      waveGradient.addColorStop(0, 'transparent');
      waveGradient.addColorStop(0.5, 'rgba(163, 229, 224, 0.3)');
      waveGradient.addColorStop(1, 'transparent');
      ctx.fillStyle = waveGradient;
      ctx.fillRect(0, waveY - 15, rect.width, 30);
    }

    // Update and draw particles
    particles.forEach((particle) => {
      // Check if particle should be validated based on wave position
      if (!particle.validated && particle.y < waveY - 10) {
        particle.validated = true;
      }

      // Draw particle
      ctx.beginPath();
      ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);

      if (particle.validated) {
        // Validated: colorful with glow
        ctx.fillStyle = particle.color;
        ctx.globalAlpha = 0.9;
        ctx.fill();

        // Add white border
        ctx.strokeStyle = 'white';
        ctx.lineWidth = 2;
        ctx.globalAlpha = 1;
        ctx.stroke();

        // Draw checkmark on validated bubbles
        ctx.strokeStyle = '#1E3A5F';
        ctx.lineWidth = 2;
        ctx.lineCap = 'round';
        ctx.lineJoin = 'round';
        ctx.beginPath();
        ctx.moveTo(particle.x - 4, particle.y);
        ctx.lineTo(particle.x - 1, particle.y + 3);
        ctx.lineTo(particle.x + 4, particle.y - 3);
        ctx.stroke();
      } else {
        // Unvalidated: gray and muted
        ctx.fillStyle = '#E5E7EB';
        ctx.globalAlpha = 0.6;
        ctx.fill();
        ctx.globalAlpha = 1;
      }
    });

  } else if (isGravity && particles.length > 0) {
    // Gravity layout - particles gravitate towards a central TEKS box
    const centerX = rect.width / 2;
    const centerY = rect.height / 2;

    // Animate particles towards their targets
    particles.forEach((particle) => {
      // Calculate distance to target
      const dx = particle.targetX - particle.x;
      const dy = particle.targetY - particle.y;
      const distance = Math.sqrt(dx * dx + dy * dy);

      // Apply gravity force
      if (distance > 1) {
        // Normalize direction vector
        const dirX = dx / distance;
        const dirY = dy / distance;

        const force = 0.08; // Gravity strength (very gentle)
        particle.velocity.x += dirX * force;
        particle.velocity.y += dirY * force;

        // Apply damping (friction) - lower value = MORE friction
        particle.velocity.x *= 0.92;
        particle.velocity.y *= 0.92;

        // Update position
        particle.x += particle.velocity.x;
        particle.y += particle.velocity.y;
      } else {
        // Snap to target when close enough
        particle.x = particle.targetX;
        particle.y = particle.targetY;
        particle.velocity.x = 0;
        particle.velocity.y = 0;
      }

      // Draw particle
      ctx.beginPath();
      ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
      ctx.fillStyle = particle.color;
      ctx.globalAlpha = 0.85;
      ctx.fill();
      ctx.globalAlpha = 1;
    });

    // Draw central box ON TOP of particles
    const boxWidth = 280;
    const boxHeight = 80;
    const boxX = centerX - boxWidth / 2;
    const boxY = centerY - boxHeight / 2;

    // Draw box background
    ctx.fillStyle = 'white';
    ctx.shadowColor = 'rgba(0, 0, 0, 0.1)';
    ctx.shadowBlur = 12;
    ctx.shadowOffsetX = 0;
    ctx.shadowOffsetY = 2;
    ctx.fillRect(boxX, boxY, boxWidth, boxHeight);
    ctx.shadowBlur = 0;

    // Draw box border
    ctx.strokeStyle = '#1E3A5F';
    ctx.lineWidth = 2;
    ctx.strokeRect(boxX, boxY, boxWidth, boxHeight);

    // Draw box text
    ctx.fillStyle = '#1E3A5F';
    ctx.font = 'bold 14px system-ui, sans-serif';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText('Texas Essential Knowledge', centerX, centerY - 10);
    ctx.fillText('and Skills', centerX, centerY + 10);

  } else {
    // Regular particle drawing
    particles.forEach((particle) => {
      // Only animate if not static
      if (!particle.isStatic) {
        // Check if this is a checklist particle
        if (particle.checkTime !== undefined) {
          // Update checked state based on elapsed time
          if (!particle.checked && elapsedTime >= particle.checkTime) {
            particle.checked = true;
            particle.color = '#A3E5E0'; // Teal when checked
          }
        }
        // Check if this is a fission pulse particle
        else if (particle.pulsePhase !== undefined && particle.baseRadius !== undefined && particle.pulseAmplitude !== undefined) {
          // Fission pulse animation - waves emanating from center
          const pulseOffset = Math.sin(animationTime * (particle.pulseSpeed || 0.03) * 60 + particle.pulsePhase) * particle.pulseAmplitude;
          const currentRadius = particle.baseRadius + pulseOffset;
          
          particle.x = (particle.centerX || 0) + Math.cos(particle.angle || 0) * currentRadius;
          particle.y = (particle.centerY || 0) + Math.sin(particle.angle || 0) * currentRadius;
        }
        // Check if this is an orbital particle (old style)
        else if (particle.angle !== undefined && particle.orbitRadius !== undefined && particle.orbitSpeed !== undefined && particle.orbitSpeed !== 0) {
          // Orbital animation - particles rotate around center
          particle.angle += particle.orbitSpeed;
          particle.x = (particle.centerX || 0) + Math.cos(particle.angle) * particle.orbitRadius;
          particle.y = (particle.centerY || 0) + Math.sin(particle.angle) * particle.orbitRadius;
        } else {
          // Regular bouncing animation
          particle.x += particle.velocity.x;
          particle.y += particle.velocity.y;

          // Bounce off edges
          if (particle.x <= particle.radius || particle.x >= rect.width - particle.radius) {
            particle.velocity.x *= -1;
          }
          if (particle.y <= particle.radius || particle.y >= rect.height - particle.radius) {
            particle.velocity.y *= -1;
          }
        }
      }

      // Draw particle (circle)
      ctx.beginPath();
      ctx.arc(particle.x, particle.y, particle.radius, 0, Math.PI * 2);
      ctx.fillStyle = particle.color;
      ctx.globalAlpha = 0.85;
      ctx.fill();
      ctx.globalAlpha = 1;
      
      // Draw checkmark if this particle is checked (for checklist only, not dots)
      if (particle.checked && particle.radius >= 10) {
        ctx.beginPath();
        ctx.strokeStyle = 'white';
        ctx.lineWidth = 2;
        ctx.lineCap = 'round';
        ctx.lineJoin = 'round';
        
        // Draw checkmark
        const r = particle.radius * 0.5;
        const cx = particle.x;
        const cy = particle.y;
        
        ctx.moveTo(cx - r * 0.6, cy);
        ctx.lineTo(cx - r * 0.1, cy + r * 0.5);
        ctx.lineTo(cx + r * 0.7, cy - r * 0.4);
        ctx.stroke();
      }
    });
  }

  animationId = requestAnimationFrame(drawParticles);
}

function handleKeydown(e: KeyboardEvent) {
  if (e.code === 'Space' || e.code === 'ArrowRight') {
    e.preventDefault();
    goNext();
  } else if (e.code === 'ArrowLeft') {
    e.preventDefault();
    goBack();
  }
}

function handleResize() {
  initParticles();
}

onMounted(() => {
  nextTick(() => {
    requestAnimationFrame(() => {
      initParticles();
    });
  });
  window.addEventListener('keydown', handleKeydown);
  window.addEventListener('resize', handleResize);
});

onUnmounted(() => {
  if (animationId) {
    cancelAnimationFrame(animationId);
  }
  window.removeEventListener('keydown', handleKeydown);
  window.removeEventListener('resize', handleResize);
});
</script>

<style scoped>
/* Wayground Impact Kit – Clean Grid Design */
.impact-story-wrapper {
  --color-bg: #F3EFDA;
  --color-text: #1E3A5F;
  --color-muted: #6B7C93;
  --color-accent: #1E3A5F;
  --color-highlight: #1E3A5F;
  --color-grid: rgba(30, 58, 95, 0.06);
  --font-display: 'DM Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-body: 'DM Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

  position: relative;
  width: 100%;
  height: 600px;
  font-family: var(--font-body);
  background: var(--color-bg);
  color: var(--color-text);
  border-radius: 12px;
  overflow: hidden;
}

/* Grid background */
.grid-background {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(var(--color-grid) 1px, transparent 1px),
    linear-gradient(90deg, var(--color-grid) 1px, transparent 1px);
  background-size: 24px 24px;
  pointer-events: none;
  z-index: 0;
}

/* No horizontal padding: parent (section-beige) provides 3.25rem / 2rem so content aligns with partnership section */
.container {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  max-width: 100%;
  margin: 0;
  padding: 1rem 0;
  box-sizing: border-box;
}

.story {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  min-height: 0;
}

/* Progress */
.progress-bar {
  height: 4px;
  background: rgba(0, 0, 0, 0.06);
  border-radius: 2px;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--color-accent), var(--color-highlight));
  border-radius: 2px;
  transition: width 0.4s ease;
}

/* Narrative - Above viz */
.narrative {
  text-align: center;
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  transition: opacity 0.15s;
  flex-shrink: 0;
}

.state-label {
  display: inline-block;
  font-size: 0.6rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--color-accent);
  margin-bottom: 0.4rem;
}

.headline {
  font-family: var(--font-display);
  font-size: 1.55rem;
  font-weight: 500;
  line-height: 1.35;
  margin: 0.25rem 0 0.5rem;
}
.headline--slide3 {
  font-size: 2rem;
}

.headline :deep(.highlight) {
  font-weight: 700;
  font-size: 1.45em;
  color: #FF319F;
}

/* 40: pink, heartbeat glow */
.headline :deep(.highlight--dot-glow) {
  color: #FF319F;
  font-size: 1.8em;
  font-weight: 800;
  text-shadow: 0 0 12px rgba(255, 49, 159, 0.6), 0 0 24px rgba(255, 49, 159, 0.35);
  animation: heartbeatGlow 1.2s ease-in-out infinite;
}
@keyframes heartbeatGlow {
  0%, 100% { text-shadow: 0 0 12px rgba(255, 49, 159, 0.6), 0 0 24px rgba(255, 49, 159, 0.35); }
  14% { text-shadow: 0 0 20px rgba(255, 49, 159, 0.9), 0 0 40px rgba(255, 49, 159, 0.5); }
  28% { text-shadow: 0 0 12px rgba(255, 49, 159, 0.6), 0 0 24px rgba(255, 49, 159, 0.35); }
  42% { text-shadow: 0 0 20px rgba(255, 49, 159, 0.9), 0 0 40px rgba(255, 49, 159, 0.5); }
  56% { text-shadow: 0 0 12px rgba(255, 49, 159, 0.6), 0 0 24px rgba(255, 49, 159, 0.35); }
  70%, 100% { text-shadow: 0 0 12px rgba(255, 49, 159, 0.6), 0 0 24px rgba(255, 49, 159, 0.35); }
}

.body-text {
  font-size: 0.95rem;
  color: var(--color-muted);
  margin: 0;
  line-height: 1.6;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}
.body-text-hero {
  font-size: 1.05rem;
  color: #FF319F;
  font-weight: 500;
}

.narrative-bridge {
  font-size: 0.85rem;
  color: var(--color-muted);
  margin: 0.5rem 0 0;
  font-weight: 500;
  letter-spacing: 0.02em;
}

/* Viz Container - White card (full width) */
.viz-container {
  flex: 1;
  position: relative;
  min-height: 320px;
  display: flex;
  flex-direction: column;
}

/* Three pillars: daily practice, student achievement, high-impact results */
.viz-inner--three-pillars {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
  gap: 1.5rem;
  padding: 1.75rem 1rem 1.5rem;
  min-height: 280px;
}
.three-pillars {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  align-items: start;
  justify-items: center;
  gap: 2.5rem;
  width: 100%;
  max-width: 960px;
  flex: 1;
  margin-top: 1rem;
}
.pillar {
  display: grid;
  grid-template-rows: 152px auto;
  align-items: start;
  justify-items: center;
  gap: 0.85rem 0;
  width: 100%;
  max-width: 240px;
  min-height: 0;
}
.pillar-visual {
  position: relative;
  width: 152px;
  height: 152px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  grid-row: 1;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.6);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  overflow: visible;
}
.pillar-icon {
  position: relative;
  z-index: 1;
  width: 72px;
  height: 72px;
  color: #1a1a2e;
  animation: pillarIconFloat 2.8s ease-in-out infinite;
}
.pillar--daily .pillar-icon { animation-delay: 0s; color: #FF319F; }
.pillar--achievement .pillar-icon { animation-delay: 0.15s; color: #7c3aed; }
.pillar--impact .pillar-icon { animation-delay: 0.3s; color: #0d9488; }
.pillar--insights .pillar-icon { animation-delay: 0s; color: #0ea5e9; }
.pillar--gaps .pillar-icon { animation-delay: 0.15s; color: #10b981; }
.pillar--smallgroup .pillar-icon { animation-delay: 0.3s; color: #8b5cf6; }
.pillar--access .pillar-icon { animation-delay: 0s; color: #f59e0b; }
.pillar--support .pillar-icon { animation-delay: 0.15s; color: #ef4444; }
.pillar--inclusive .pillar-icon { animation-delay: 0.3s; color: #06b6d4; }
.pillar--standards .pillar-icon { animation-delay: 0s; color: #6366f1; }
.pillar--targets .pillar-icon { animation-delay: 0.15s; color: #eab308; }
.pillar--readiness .pillar-icon { animation-delay: 0.3s; color: #22c55e; }
.pillar--persistence .pillar-icon { animation-delay: 0s; color: #f97316; }
.pillar--reattempts .pillar-icon { animation-delay: 0.15s; color: #3b82f6; }
.pillar--outcomes .pillar-icon { animation-delay: 0.3s; color: #10b981; }
@keyframes pillarIconFloat {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-4px); }
}
.pillar-title {
  grid-row: 2;
  font-size: 1rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0;
  letter-spacing: -0.02em;
  text-align: center;
  line-height: 1.3;
  min-height: 2.4em;
  display: block;
}
.pillar-title :deep(.pillar-title-key) {
  color: #2563eb;
  font-weight: 700;
  font-size: inherit;
  line-height: inherit;
}
.pillar-statement {
  text-align: center;
  font-size: 1.08rem;
  line-height: 1.55;
  font-weight: 600;
  color: #334155;
  margin: 0;
  margin-top: auto;
  padding: 3.5rem 0.5rem 1.5rem;
  max-width: 560px;
  width: 100%;
  box-sizing: border-box;
}
.pillar-statement :deep(.pillar-statement-highlight) {
  color: #FF319F;
}

/* Page 1: Rigorous Practice – dots pulse in sequence */
.daily-dots {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
.daily-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #FF319F;
  box-shadow: 0 0 12px rgba(255, 49, 159, 0.4);
  opacity: 0.5;
  animation: dailyDotPulse 1.4s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.12s);
}
@keyframes dailyDotPulse {
  0%, 100% { transform: scale(0.85); opacity: 0.4; }
  50% { transform: scale(1.15); opacity: 1; }
}

/* Page 2: You sparked engagement – sparkles around icon */
.engagement-sparkles {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.engagement-sparkle {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #FF319F;
  box-shadow: 0 0 14px rgba(255, 49, 159, 0.6);
  opacity: 0.6;
  animation: sparklePulse 1.2s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.1s);
}
@keyframes sparklePulse {
  0%, 100% { transform: scale(0.7); opacity: 0.4; }
  50% { transform: scale(1.2); opacity: 1; }
}

/* 2. Student Achievement: bars with gradient and clearer growth */
.achievement-bars {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: flex-end;
  gap: 12px;
  height: 72px;
}
.achievement-bar {
  width: 18px;
  height: var(--h, 50%);
  min-height: 12px;
  background: linear-gradient(180deg, #a78bfa 0%, #7c3aed 100%);
  border-radius: 6px 6px 0 0;
  transform-origin: bottom;
  opacity: 0.9;
  box-shadow: 0 -2px 8px rgba(124, 58, 237, 0.25);
  animation: achievementBarGrow 1.6s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.12s);
}
@keyframes achievementBarGrow {
  0%, 100% { transform: scaleY(0.5); }
  50% { transform: scaleY(1); }
}

/* Page 1: High-Impact Results – single pulse ring */
.impact-pulse {
  position: absolute;
  width: 88px;
  height: 88px;
  border-radius: 50%;
  border: 2px solid #0d9488;
  opacity: 0;
  box-shadow: 0 0 0 0 rgba(13, 148, 136, 0.2);
  animation: impactPulse 2.2s ease-out infinite;
}
@keyframes impactPulse {
  0% { transform: scale(0.5); opacity: 0.6; }
  100% { transform: scale(1.6); opacity: 0; }
}

/* Page 2: You inspired shared success – two overlapping pulse rings */
.success-pulse {
  position: absolute;
  width: 88px;
  height: 88px;
  border-radius: 50%;
  border: 2px solid #0d9488;
  opacity: 0;
  box-shadow: 0 0 0 0 rgba(13, 148, 136, 0.2);
  animation: successPulse 2.2s ease-out infinite;
}
.success-pulse--2 {
  animation-delay: 0.5s;
}
@keyframes successPulse {
  0% { transform: scale(0.5); opacity: 0.5; }
  100% { transform: scale(1.5); opacity: 0; }
}

/* Page 3: You turned insights into action – rising line + arrow */
.insights-action-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.insights-line {
  position: absolute;
  width: 2px;
  height: 36px;
  background: linear-gradient(to top, #0ea5e9 0%, rgba(14, 165, 233, 0.2) 100%);
  border-radius: 2px;
  bottom: 38%;
  left: 50%;
  transform: translateX(-50%);
  animation: insightsRise 1.8s ease-in-out infinite;
}
.insights-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  border-bottom: 12px solid #0ea5e9;
  bottom: 52%;
  left: 50%;
  transform: translateX(-50%);
  opacity: 0.9;
  animation: insightsRise 1.8s ease-in-out infinite;
}
@keyframes insightsRise {
  0%, 100% { transform: translateX(-50%) translateY(0); opacity: 0.7; }
  50% { transform: translateX(-50%) translateY(-6px); opacity: 1; }
}

/* Page 3: You closed achievement gaps – two bars leveling */
.gap-close-bars {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: flex-end;
  gap: 20px;
  height: 72px;
}
.gap-bar {
  width: 20px;
  border-radius: 6px 6px 0 0;
  transform-origin: bottom;
  background: linear-gradient(180deg, #34d399 0%, #10b981 100%);
  box-shadow: 0 -2px 8px rgba(16, 185, 129, 0.3);
}
.gap-bar--short {
  height: 28%;
  min-height: 14px;
  animation: gapBarGrow 2s ease-in-out infinite;
}
.gap-bar--tall {
  height: 85%;
  animation: gapBarHold 2s ease-in-out infinite;
}
@keyframes gapBarGrow {
  0%, 100% { transform: scaleY(0.35); }
  50% { transform: scaleY(1); }
}
@keyframes gapBarHold {
  0%, 100% { transform: scaleY(1); }
  50% { transform: scaleY(0.9); }
}

/* Page 3: You targeted small-group support – cluster of dots + ring */
.small-group-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.small-group-dot {
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #8b5cf6;
  box-shadow: 0 0 10px rgba(139, 92, 246, 0.5);
  animation: smallGroupPulse 1.5s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.2s);
}
.small-group-dot:nth-child(1) { top: 42%; left: 42%; }
.small-group-dot:nth-child(2) { top: 38%; left: 52%; }
.small-group-dot:nth-child(3) { top: 48%; left: 48%; }
.small-group-ring {
  position: absolute;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  border: 2px dashed rgba(139, 92, 246, 0.5);
  animation: smallGroupRing 3s linear infinite;
}
@keyframes smallGroupPulse {
  0%, 100% { transform: scale(0.9); opacity: 0.8; }
  50% { transform: scale(1.1); opacity: 1; }
}
@keyframes smallGroupRing {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/* Page 4: You expanded access – expanding rings */
.access-expand-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.access-ring {
  position: absolute;
  border-radius: 50%;
  border: 2px solid rgba(245, 158, 11, 0.5);
  animation: accessExpand 2.5s ease-out infinite;
}
.access-ring--1 { width: 40px; height: 40px; animation-delay: 0s; }
.access-ring--2 { width: 40px; height: 40px; animation-delay: 0.4s; }
.access-ring--3 { width: 40px; height: 40px; animation-delay: 0.8s; }
@keyframes accessExpand {
  0% { transform: scale(0.4); opacity: 0.8; }
  100% { transform: scale(2.2); opacity: 0; }
}

/* Page 4: You provided moments of accessible support – gentle pulses */
.support-moments-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
}
.support-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #ef4444;
  box-shadow: 0 0 12px rgba(239, 68, 68, 0.4);
  opacity: 0.7;
  animation: supportPulse 1.6s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.2s);
}
@keyframes supportPulse {
  0%, 100% { transform: scale(0.85); opacity: 0.5; }
  50% { transform: scale(1.15); opacity: 1; }
}

/* Page 4: You built an inclusive classroom – circles coming together */
.inclusive-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.inclusive-circle {
  position: absolute;
  border-radius: 50%;
  background: rgba(6, 182, 212, 0.4);
  animation: inclusiveGather 2s ease-in-out infinite;
}
.inclusive-circle--1 { width: 28px; height: 28px; top: 38%; left: 38%; animation-delay: 0s; }
.inclusive-circle--2 { width: 24px; height: 24px; top: 42%; left: 50%; animation-delay: 0.25s; }
.inclusive-circle--3 { width: 26px; height: 26px; top: 50%; left: 42%; animation-delay: 0.5s; }
@keyframes inclusiveGather {
  0%, 100% { transform: scale(0.9); opacity: 0.5; }
  50% { transform: scale(1.1); opacity: 0.9; }
}

/* Page 5: You mirrored state standards – two aligned bars */
.standards-mirror-viz {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 24px;
}
.mirror-bar {
  width: 56px;
  height: 8px;
  border-radius: 4px;
  background: linear-gradient(90deg, rgba(99, 102, 241, 0.4) 0%, #6366f1 50%, rgba(99, 102, 241, 0.4) 100%);
  animation: mirrorAlign 2s ease-in-out infinite;
}
.mirror-bar--bottom {
  animation-delay: 0.15s;
}
@keyframes mirrorAlign {
  0%, 100% { opacity: 0.7; transform: scaleX(0.95); }
  50% { opacity: 1; transform: scaleX(1); }
}

/* Page 5: You hit curriculum targets – bullseye rings */
.targets-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.target-ring {
  position: absolute;
  border-radius: 50%;
  border: 2px solid rgba(234, 179, 8, 0.6);
  animation: targetPulse 1.8s ease-in-out infinite;
}
.target-ring--1 { width: 70px; height: 70px; animation-delay: 0s; }
.target-ring--2 { width: 48px; height: 48px; animation-delay: 0.2s; }
.target-ring--3 { width: 26px; height: 26px; animation-delay: 0.4s; }
.target-bullseye {
  position: absolute;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #eab308;
  box-shadow: 0 0 12px rgba(234, 179, 8, 0.6);
  animation: bullseyeGlow 1.2s ease-in-out infinite;
}
@keyframes targetPulse {
  0%, 100% { opacity: 0.5; transform: scale(0.98); }
  50% { opacity: 1; transform: scale(1); }
}
@keyframes bullseyeGlow {
  0%, 100% { opacity: 0.9; box-shadow: 0 0 8px rgba(234, 179, 8, 0.5); }
  50% { opacity: 1; box-shadow: 0 0 16px rgba(234, 179, 8, 0.8); }
}

/* Page 5: You verified test readiness – checkmarks */
.readiness-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.readiness-check {
  width: 20px;
  height: 20px;
  border: 2px solid #22c55e;
  border-radius: 4px;
  background: transparent;
  position: relative;
  animation: readinessCheck 1.4s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.2s);
}
.readiness-check::after {
  content: '';
  position: absolute;
  left: 4px;
  top: 1px;
  width: 6px;
  height: 10px;
  border: solid #22c55e;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
  opacity: 0;
  animation: checkAppear 1.4s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.2s);
}
@keyframes readinessCheck {
  0%, 40% { transform: scale(0.9); opacity: 0.7; }
  50%, 100% { transform: scale(1); opacity: 1; }
}
@keyframes checkAppear {
  0%, 30% { opacity: 0; }
  50%, 100% { opacity: 1; }
}

/* Page 6: You powered persistence – steady line + moving dot */
.persistence-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.persistence-line {
  position: absolute;
  width: 80px;
  height: 4px;
  background: linear-gradient(90deg, rgba(249, 115, 22, 0.3) 0%, #f97316 50%, rgba(249, 115, 22, 0.3) 100%);
  border-radius: 2px;
  animation: persistenceGlow 2s ease-in-out infinite;
}
.persistence-dot {
  position: absolute;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: #f97316;
  box-shadow: 0 0 14px rgba(249, 115, 22, 0.6);
  animation: persistenceMove 2.2s ease-in-out infinite;
}
@keyframes persistenceGlow {
  0%, 100% { opacity: 0.8; }
  50% { opacity: 1; }
}
@keyframes persistenceMove {
  0% { transform: translateX(-32px); }
  50% { transform: translateX(0); }
  100% { transform: translateX(32px); }
}

/* Page 6: You championed reattempts – circular retry arrows */
.reattempts-viz {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
.reattempt-arrow {
  position: absolute;
  width: 36px;
  height: 36px;
  border: 2px solid rgba(59, 130, 246, 0.6);
  border-top-color: transparent;
  border-right-color: transparent;
  border-radius: 50%;
  animation: reattemptSpin 1.8s linear infinite;
}
.reattempt-arrow--2 {
  width: 28px;
  height: 28px;
  animation-duration: 2.2s;
  animation-direction: reverse;
}
@keyframes reattemptSpin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

/* Page 6: You maximized outcomes – bars with one at max */
.outcomes-viz {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: flex-end;
  gap: 14px;
  height: 72px;
}
.outcome-bar {
  width: 18px;
  height: var(--h, 50%);
  min-height: 10px;
  background: linear-gradient(180deg, rgba(16, 185, 129, 0.5) 0%, #10b981 100%);
  border-radius: 6px 6px 0 0;
  transform-origin: bottom;
  animation: outcomeGrow 2s ease-in-out infinite;
  animation-delay: calc(var(--i, 0) * 0.15s);
}
.outcome-bar--max {
  box-shadow: 0 -2px 12px rgba(16, 185, 129, 0.4);
}
.outcome-bar:nth-child(1) { animation-delay: 0s; }
.outcome-bar:nth-child(2) { animation-delay: 0.2s; }
.outcome-bar:nth-child(3) { animation-delay: 0.4s; }
@keyframes outcomeGrow {
  0%, 100% { transform: scaleY(0.85); }
  50% { transform: scaleY(1); }
}

/* Inner area: canvas + overlays (dots and slide content) */
.viz-inner {
  position: relative;
  flex: 1;
  min-height: 250px;
  min-width: 0;
  width: 100%;
  box-sizing: border-box;
}

/* Slide 1: two columns – left = bubbles, right = impact list */
.viz-inner--split {
  display: flex;
  flex-direction: row;
  align-items: stretch;
  gap: 0;
}
.viz-bubble-column {
  position: relative;
  flex: 1;
  min-width: 0;
  min-height: 250px;
  overflow: hidden;
}
.viz-inner--split .viz-bubble-column {
  flex: 0 0 54%;
  min-height: 250px;
}
.viz-impact-column {
  flex: 0 0 46%;
  padding: 1rem 1.25rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-width: 0;
  border-left: 1px solid #e2e8f0;
}
.viz-impact-heading {
  font-size: 1.05rem;
  font-weight: 700;
  color: #1a1a2e;
  margin: 0 0 0.75rem;
  line-height: 1.3;
  letter-spacing: -0.02em;
}
.viz-impact-heading--animate {
  animation: viz-impact-heading-in 0.55s ease-out;
}
@keyframes viz-impact-heading-in {
  from {
    opacity: 0;
    transform: translateY(6px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
.viz-impact-heading :deep(.highlight) {
  color: #FF319F;
}
.viz-impact-list {
  margin: 0;
  padding-left: 1.25rem;
  list-style: disc;
  font-size: 0.95rem;
  color: #334155;
  line-height: 1.7;
}
.viz-impact-list--animate li {
  animation: viz-impact-heading-in 0.55s ease-out both;
}
.viz-impact-list--animate li:nth-child(1) { animation-delay: 0.1s; }
.viz-impact-list--animate li:nth-child(2) { animation-delay: 0.2s; }
.viz-impact-list--animate li:nth-child(3) { animation-delay: 0.3s; }
.viz-impact-list--animate li:nth-child(4) { animation-delay: 0.4s; }
.viz-impact-list--animate li:nth-child(5) { animation-delay: 0.5s; }
.viz-impact-list--animate li:nth-child(6) { animation-delay: 0.6s; }
.viz-impact-list li {
  margin-bottom: 0.4rem;
}
.viz-impact-list li:last-child {
  margin-bottom: 0;
}

.particle-canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
}

/* Curly arrows + statements – inside white card, close to bubbles, not on border */
.bubble-arrows-wrap {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 2;
  box-sizing: border-box;
}
.arrow-block {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
}
.arrow-block .curly-arrow {
  width: 88px;
  height: 64px;
  overflow: visible;
  flex-shrink: 0;
  color: #1e293b;
}
.arrow-block .arrow-line {
  stroke: currentColor;
  stroke-width: 2.5;
  fill: none;
}
.arrow-block .arrow-head {
  fill: currentColor;
  stroke: currentColor;
  stroke-width: 0.8;
  stroke-linejoin: round;
}
.arrow-tl {
  top: 10%;
  left: 6%;
  align-items: flex-start;
}
.arrow-tl .bubble-label { align-self: flex-start; margin-top: 2px; }
.arrow-tr {
  top: 10%;
  right: 6%;
  align-items: flex-end;
}
.arrow-tr .bubble-label { align-self: flex-end; text-align: right; margin-top: 2px; }
.arrow-bl {
  bottom: 10%;
  left: 6%;
  align-items: flex-start;
}
.arrow-bl .bubble-label { align-self: flex-start; margin-top: 2px; }
.arrow-br {
  bottom: 10%;
  right: 6%;
  align-items: flex-end;
}
.arrow-br .bubble-label { align-self: flex-end; text-align: right; margin-top: 2px; }
.bubble-arrows-wrap .bubble-label {
  display: inline-flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 6px;
  font-size: 0.8rem;
  line-height: 1.3;
  color: #1a1a2e;
  font-weight: 400;
  white-space: normal;
  max-width: 9em;
  opacity: 0;
  animation: bubbleLabelIn 0.45s ease-out forwards;
  animation-delay: calc(0.1s * var(--i, 0));
}
.bubble-arrows-wrap .bubble-label .label-emoji {
  flex-shrink: 0;
  width: 1.15em;
  min-height: 1.15em;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 1em;
  line-height: 1;
}

/* Slide 1: outcome statements read as achievements from 40 games */
.bubble-arrows-wrap--outcomes .bubble-label {
  font-weight: 600;
  font-size: 0.85rem;
  color: #1a1a2e;
  padding: 0.35rem 0.5rem;
  background: rgba(255, 49, 159, 0.06);
  border-radius: 8px;
  border-left: 3px solid #FF319F;
  max-width: 10em;
}

@keyframes bubbleLabelIn {
  from { opacity: 0; transform: translateY(4px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Data Mosaic (bento grid) - slide 3 */
.data-mosaic {
  position: absolute;
  inset: 0;
  padding: 1.25rem;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
  pointer-events: none;
  box-sizing: border-box;
}

.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 1fr);
  gap: 6px;
  width: 100%;
  max-width: 420px;
  max-height: 280px;
  aspect-ratio: 3/2;
}

.bento-cell {
  min-height: 0;
  border-radius: 6px;
  background: var(--viz-bg, #f8f7f4);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.06);
  opacity: 0;
  transform: scale(0.82);
  animation: bentoPopIn 0.5s cubic-bezier(0.34, 1.4, 0.64, 1) forwards;
  animation-delay: calc(0.06s * var(--bento-i, 0));
}

@keyframes bentoPopIn {
  from {
    opacity: 0;
    transform: scale(0.82);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.bento-cell--wide { grid-column: span 2; }
.bento-cell--tall { grid-row: span 2; }
.bento-cell--wide.bento-cell--tall { grid-column: span 2; grid-row: span 2; }

/* Pastel palette for mosaic */
.bento-cell--pattern.bento-cell--dots {
  background-color: #E8E4F0;
  background-image: radial-gradient(circle, #A3E5E0 1.2px, transparent 1.2px);
  background-size: 10px 10px;
}
.bento-cell--pattern.bento-cell--dots.bento-cell--alt {
  background-color: #FFD8B2;
  background-image: radial-gradient(circle, rgba(0,0,0,0.12) 1px, transparent 1px);
  background-size: 8px 8px;
}
.bento-cell--pattern.bento-cell--lines {
  background: repeating-linear-gradient(
    -55deg,
    transparent,
    transparent 4px,
    rgba(163, 229, 224, 0.4) 4px,
    rgba(163, 229, 224, 0.4) 6px
  );
  background-color: #ECEB75;
}
.bento-cell--pattern.bento-cell--grid {
  background-color: #f5f3ef;
  background-image:
    linear-gradient(rgba(220, 210, 239, 0.3) 1px, transparent 1px),
    linear-gradient(90deg, rgba(220, 210, 239, 0.3) 1px, transparent 1px);
  background-size: 8px 8px;
}
.bento-cell--pattern.bento-cell--gradient {
  background: linear-gradient(135deg, #A3E5E0 0%, #DCD2EF 50%, #FFD8B2 100%);
}
.bento-cell--pattern.bento-cell--gradient.bento-cell--alt {
  background: linear-gradient(220deg, #ECEB75 0%, #A3E5E0 100%);
}
.bento-cell--pattern.bento-cell--noise {
  background: linear-gradient(145deg, #DCD2EF 0%, #E8E4F0 50%, #f0eef5 100%);
  box-shadow: inset 0 0 0 1px rgba(220, 210, 239, 0.4);
}
.bento-cell--pattern.bento-cell--diagonal {
  background: repeating-linear-gradient(
    45deg,
    transparent,
    transparent 6px,
    rgba(255, 216, 178, 0.5) 6px,
    rgba(255, 216, 178, 0.5) 8px
  );
  background-color: #f8f7f4;
}

.bento-cell--icon {
  display: flex;
  align-items: center;
  justify-content: center;
  color: #5a5a72;
}
.bento-cell--icon .bento-icon {
  width: 22px;
  height: 22px;
  opacity: 0.85;
  animation: bentoIconIn 0.4s ease-out calc(0.06s * var(--bento-i, 0) + 0.15s) both;
}

@keyframes bentoIconIn {
  from {
    opacity: 0;
    transform: scale(0.5);
  }
  to {
    opacity: 0.85;
    transform: scale(1);
  }
}

.bento-cell--icon .bento-icon--glow {
  animation: bentoIconIn 0.4s ease-out calc(0.06s * var(--bento-i, 0) + 0.15s) both,
    bentoGlow 2.5s ease-in-out 1s infinite;
}

@keyframes bentoGlow {
  0%, 100% { opacity: 0.85; filter: brightness(1); }
  50% { opacity: 1; filter: brightness(1.15); }
}
.bento-cell--icon.bento-cell--book { background: #E8E4F0; color: #6B5B95; }
.bento-cell--icon.bento-cell--check { background: #d4f1e8; color: #0d7a5a; }
.bento-cell--icon.bento-cell--lightbulb { background: #fff4e0; color: #b8860b; }
.bento-cell--icon.bento-cell--book.bento-cell--alt { background: #f0eef5; color: #7c6ba8; }

/* Oakland Middle School slide (slide 6) - feature cards */
.oakland-slide {
  position: absolute;
  inset: 0;
  padding: 0.5rem 0.75rem;
  overflow: hidden;
  z-index: 2;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
}

.oakland-cards {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-auto-rows: 1fr;
  gap: 0.5rem;
  width: 100%;
  max-width: 560px;
  max-height: 100%;
  margin: 0 auto;
  align-items: stretch;
}

.oakland-card {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  background: #fff;
  border-radius: 8px;
  padding: 0.6rem 0.65rem;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.06);
  border: 1px solid rgba(0, 0, 0, 0.06);
  text-align: left;
  opacity: 0;
  transform: translateY(8px);
  animation: oaklandCardIn 0.4s ease-out forwards;
  animation-delay: calc(0.05s * var(--card-i, 0));
  min-height: 0;
}

@keyframes oaklandCardIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.oakland-card-icon {
  width: 28px;
  height: 28px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #1e293b;
  background: linear-gradient(135deg, #E8E4F0 0%, #f0eef5 100%);
  margin-bottom: 0.35rem;
}

.oakland-card-icon svg {
  width: 14px;
  height: 14px;
}

.oakland-card-heading {
  font-family: var(--font-display);
  font-size: 0.78rem;
  font-weight: 600;
  color: #FF319F;
  margin: 0 0 0.25rem;
  line-height: 1.25;
}

.oakland-card-line1,
.oakland-card-line2,
.oakland-card-line {
  font-size: 0.65rem;
  color: #64748b;
  line-height: 1.35;
  margin: 0;
}

.oakland-card-line2,
.oakland-card-line {
  margin-top: 0.1rem;
}

@media (min-width: 520px) {
  .oakland-cards {
    grid-template-columns: repeat(3, 1fr);
    gap: 0.5rem;
  }
}

/* Central stat display */
.stat-display {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  opacity: 0;
  transition: opacity 0.4s ease;
  z-index: 2;
}

.stat-display.visible {
  opacity: 1;
}

.stat-value {
  display: block;
  font-family: var(--font-display);
  font-size: 4rem;
  font-weight: 700;
  line-height: 1;
  color: var(--color-accent);
  margin-bottom: 8px;
}

.stat-label {
  display: block;
  font-size: 0.9rem;
  font-weight: 500;
  color: var(--color-muted);
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

/* Growth display (for Before/After slide) */
.growth-display {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  align-items: center;
  gap: 2rem;
  opacity: 0;
  transition: opacity 0.4s ease;
  z-index: 2;
}

.growth-display.visible {
  opacity: 1;
}

.growth-item {
  text-align: center;
}

.growth-item .growth-value {
  display: block;
  font-family: var(--font-display);
  font-size: 3rem;
  font-weight: 700;
  line-height: 1;
  margin-bottom: 4px;
}

.growth-item.before .growth-value {
  color: var(--color-muted);
}

.growth-item.after .growth-value {
  color: var(--color-accent);
}

.growth-label-text {
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--color-muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.growth-arrow {
  color: var(--color-accent);
}

/* Note at bottom of viz */
.viz-note {
  position: absolute;
  bottom: 12px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.7rem;
  color: var(--color-muted);
  background: rgba(255, 255, 255, 0.9);
  padding: 6px 12px;
  border-radius: 20px;
  opacity: 0;
  transition: opacity 0.3s;
  z-index: 3;
}

.viz-note.visible {
  opacity: 1;
}

.viz-note-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  flex-shrink: 0;
}

/* Constellation lines */
.constellation-lines {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

/* Controls: Back + Next at bottom */
.controls {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 0.75rem;
  padding: 1rem 1.25rem 1rem 0;
  margin-top: auto;
  margin-bottom: 1.25rem;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 10px 20px;
  font-size: 0.85rem;
  font-weight: 500;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.15s;
  font-family: inherit;
}

.btn-back {
  background: rgba(0, 0, 0, 0.05);
  color: var(--color-muted);
}

.btn-back:hover:not(:disabled) {
  background: rgba(0, 0, 0, 0.08);
}

.btn-back:disabled {
  opacity: 0.3;
  cursor: default;
}

.btn-next {
  background: #FF319F;
  color: white;
}

.btn-next:hover:not(:disabled) {
  background: #e02d8d;
}

.btn-next:disabled {
  opacity: 0.3;
  cursor: default;
}

/* Click hint */
.click-hint {
  text-align: center;
  font-size: 0.75rem;
  color: var(--color-muted);
  opacity: 0;
  transition: opacity 0.3s;
  padding-bottom: 0.5rem;
}

.click-hint.visible {
  opacity: 0.6;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 0.4;
  }
  50% {
    opacity: 0.8;
  }
}

@media (max-width: 600px) {
  .container {
    padding: 1rem 0;
  }

  .headline {
    font-size: 1.25rem;
  }

  .body-text {
    font-size: 0.9rem;
  }

  .viz-container {
    min-height: 200px;
  }

  .stat-value {
    font-size: 2.5rem;
  }

  .stat-label {
    font-size: 0.75rem;
  }

  .growth-display {
    gap: 1rem;
  }

  .growth-item .growth-value {
    font-size: 2rem;
  }

  .growth-arrow svg {
    width: 32px;
    height: 16px;
  }
}
</style>
