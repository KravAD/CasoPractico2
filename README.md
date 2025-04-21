# CasoPractico2
Enlace Repositorio GitHub --> https://github.com/KravAD/CasoPractico2.git

# Cálculo de la Capacidad Teórica de los Enlaces Críticos Usando la Fórmula de Shannon

Para estimar la capacidad máxima de los enlaces más importantes de la red, se utilizó la fórmula de Shannon:

$$ C = B \cdot \log_2(1 + \text{SNR}) $$

Donde:

- **C** es la capacidad máxima del canal en bits por segundo (bps).
- **B** es el ancho de banda del canal (en este caso, 1 Gbps o \( 1 \times 10^9 \) bps, ya que todos los enlaces usan interfaces Gigabit).
- **SNR** es la relación señal a ruido en forma lineal (no en decibelios), estimada según la distancia del enlace.

A continuación se presentan los resultados calculados para cada enlace crítico identificado en la topología de red:

### Enlace entre el Switch Core y los servidores (Servers-PT) ubicados en un búnker subterráneo a 30 metros

- **Distancia:** 30 metros
- **SNR estimado:** 3162.3 (equivalente a 35 dB)
- **Capacidad teórica:** 11.63 Gbps

### Enlace entre el Switch Core y el Router de Secretaría

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (equivalente a 40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Core y el Router del Recinto

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Core y el Router de la Sala de Videoconferencia

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Core y el Router del Laboratorio

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Core y el Router Externo, que representa otro edificio a 3 km de distancia

- **Distancia:** 3 km
- **SNR estimado:** 316.2 (25 dB)
- **Capacidad teórica:** 8.31 Gbps

### Enlace entre los servidores (Servers-PT) y el Router Externo (pasando por el Switch DMZ y Switch Core)

- **Distancia:** 3 km
- **SNR estimado:** 316.2 (25 dB)
- **Capacidad teórica:** 8.31 Gbps

Estos cálculos permiten identificar los enlaces con mayor carga potencial y evaluar si el diseño actual soporta adecuadamente el tráfico de red esperado.
