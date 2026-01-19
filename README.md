from mplsoccer import Radar
import matplotlib.pyplot as plt
from matplotlib.patches import Patch

# Parametry i zakresy (dostosuj do swoich danych)
params = [
    "Bramki",
    "xG",
    "xGOT",
    "Strzały ogółem",
    "strzały celne",
    "Udane dryblingi ",
    "Wygrane pojedynki",
    "Kontakty"
]

low = [0, 0, 0, 0, 0, 0, 0, 0]
high = [3, 1, 7, 6, 5, 10, 100, 50]  # Zakresy możesz dostosować

# Dane zawodników (wpisz swoje wartości)
vini = [1, 0.61,1.24, 5, 4, 4, 5, 29]   # przykładowe wartości
raphinha = [2, 0.54, 0.72, 5, 3, 1, 82, 41]  # przykładowe wartości

# Tworzenie wykresu radarowego
radar = Radar(params, low, high, num_rings=5, ring_width=1, center_circle_radius=1)
fig, ax = radar.setup_axis(facecolor='white', figsize=(12, 10))

#Tlo z naturalnym kolorem
radar.draw_circles(ax=ax, facecolor='#eaeaea', edgecolor='#bbbbbb')
radar.draw_range_labels(ax=ax, fontsize=11)
radar.draw_param_labels(ax=ax, fontsize=13)

radar.draw_radar(vini, ax=ax,
                 kwargs_radar={'facecolor': '#6196e9', 'alpha': 0.9},
                 kwargs_rings={'facecolor': '#6196e9', 'alpha': 0.7})

radar.draw_radar(raphinha, ax=ax,
                 kwargs_radar={'facecolor': '#ec7676', 'alpha': 0.9},
                 kwargs_rings={'facecolor': '#ec7676', 'alpha': 0.7})

ax.legend(['Vini', 'Raphinha'], loc='upper right', bbox_to_anchor=(1.3, 1))
plt.title('Porównanie statystyk: Vini vs Raphinha(SuperCap Final)', fontsize=17, fontweight='bold', color='#6196e9', pad=21)
plt.savefig("radar_vini ve raphinha_mplsoccer.png", dpi=300)

plt.show()
