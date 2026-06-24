<div class="hero hero--ayerstone" markdown>

# Ayerstone
## Crown of the Falls

A floating city between worlds. A harbor of Arkflight ships. A kingdom built on stone, water, chains, magic, and dangerous ambition.

<div class="ayerstone-hero-actions">
  <a class="ayerstone-hero-button" href="districts/"><span>Explore the City</span></a>
  <a class="ayerstone-hero-button" href="houses/"><span>Great Houses</span></a>
  <a class="ayerstone-hero-button" href="player-guide/chainbound-isles/"><span>Chainbound Isles</span></a>
  <a class="ayerstone-hero-button" href="arkflight-tech/"><span>Arkflight Technology</span></a>
</div>

</div>

<div class="ayerstone-side-float">
  <img data-ayerstone-art="side" alt="Ayerstone watchtower and arkflight dock">
</div>

## Welcome to the Setting Guide

Ayerstone is a massive floating world-shard city suspended in the dark void. Arkflight ships crowd the Grand Docks, water pours endlessly from the Waterplane Portal into Portal Lake, and the Great Houses compete for influence across terraces, markets, temples, foundries, and chained satellite islands.

> Everything passes through Ayerstone Port, legal or illegal.

## Start Here

<div class="ayerstone-art-grid">
  <a class="ayerstone-art-card" href="districts/" aria-label="Open Districts">
    <img data-ayerstone-art="explore" alt="Explore the City">
    <strong>The City</strong>
    <span>Explore the major districts of Ayerstone: Crownward, Merchant Reach, Driftwall, the Grand Docks, Noble Row, Portal Lake, Brassworks, Deepstone Gate, and Waterfall Ward.</span>
  </a>
  <a class="ayerstone-art-card" href="houses/" aria-label="Open Great Houses">
    <img data-ayerstone-art="great" alt="Great Houses">
    <strong>Great Houses</strong>
    <span>Learn the noble houses that shape the city's politics, trade, food, ships, law, water, and industry.</span>
  </a>
  <a class="ayerstone-art-card" href="player-guide/chainbound-isles/" aria-label="Open Chainbound Isles">
    <img data-ayerstone-art="chain" alt="Chainbound Isles">
    <strong>Chainbound Isles</strong>
    <span>Journey beyond the main city to the chained biome-islands, including Vael'Tharis, the Isle of the Dawn-Wing.</span>
  </a>
  <a class="ayerstone-art-card" href="arkflight-tech/" aria-label="Open Arkflight Tech">
    <img data-ayerstone-art="ark" alt="Arkflight Technology">
    <strong>Arkflight Technology</strong>
    <span>Understand Arkengines, aetherite, levstone, Ark Compasses, and the magical systems that keep civilization moving through the Void.</span>
  </a>
</div>

<script>
(function () {
  var version = '20260623d';
  function loadArt(name) {
    return fetch('assets/art/inline/' + name + '.b64.txt?v=' + version, { cache: 'no-store' })
      .then(function (response) {
        if (!response.ok) throw new Error(name + ' art failed');
        return response.text();
      })
      .then(function (text) {
        return 'data:image/jpeg;base64,' + text.trim();
      });
  }

  Promise.all(['header', 'side', 'explore', 'great', 'chain', 'ark'].map(function (name) {
    return loadArt(name).then(function (url) { return [name, url]; });
  })).then(function (entries) {
    var art = {};
    entries.forEach(function (entry) { art[entry[0]] = entry[1]; });

    var hero = document.querySelector('.hero--ayerstone');
    if (hero && art.header) {
      hero.style.backgroundImage = 'linear-gradient(90deg, rgba(5,7,18,.82), rgba(9,11,26,.38), rgba(5,7,18,.82)), linear-gradient(180deg, rgba(5,7,18,.08), rgba(5,7,18,.88)), url("' + art.header + '")';
      hero.classList.add('ayerstone-art-loaded');
    }

    document.querySelectorAll('[data-ayerstone-art]').forEach(function (img) {
      var key = img.getAttribute('data-ayerstone-art');
      if (art[key]) img.src = art[key];
    });
  }).catch(function (error) {
    console.error('Ayerstone art loader failed:', error);
  });
})();
</script>

!!! note "Player-Facing Lore"
    This site is intended for player-safe material. GM secrets, hidden histories, and campaign revelations should remain outside the public guide.
