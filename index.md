/* Updated CSS for logo animation timing */

.logo-mask-container::after {
    animation: searchlight-sweep 3s linear infinite;
}

@keyframes searchlight-sweep {
  0% { transform: translateX(-100%) skewX(-20deg); }
  75% { transform: translateX(100%) skewX(-20deg); }
  100% { transform: translateX(100%) skewX(-20deg); }
}

.bi-color-title-sweep {
    animation: text-searchlight 3s linear infinite;
}

@keyframes text-searchlight {
  0% { background-position: -50% center, 0 center; }
  70% { background-position: 150% center, 0 center; }
  100% { background-position: 150% center, 0 center; }
}

.lang-zh .logo-mask-container::after {
    animation: searchlight-sweep-zh 2.5s ease-in-out infinite;
}

@keyframes searchlight-sweep-zh {
  0% { transform: translateX(-150%) skewX(-15deg); }
  75% { transform: translateX(250%) skewX(-15deg); }
  100% { transform: translateX(250%) skewX(-15deg); }
}

.lang-zh .bi-color-title-sweep {
    animation: text-searchlight-zh 2.5s ease-in-out infinite;
}

@keyframes text-searchlight-zh {
  0% { background-position: -150% center, 0 center; }
  75% { background-position: 250% center, 0 center; }
  100% { background-position: 250% center, 0 center; }
}