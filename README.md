# CasoPractico2
Enlace Repositorio GitHub --> https://github.com/KravAD/CasoPractico2.git

## Modelado de la Comunicación (OSI/TCP-IP)

| Capa OSI             | Capa TCP/IP     | Función                                                                 |
|----------------------|------------------|-------------------------------------------------------------------------|
| **Capa Física**       | Acceso a red     | Transmite los datos por un medio físico.                               |
| **Capa Enlace de datos** | Acceso a red     | Controla el flujo de datos, detecta y corrige errores e identifica dispositivos mediante direcciones MAC. |
| **Capa Red**          | Acceso a red     | Usa direcciones IP y se encarga de direccionar y enrutar los paquetes de datos. |
| **Capa Transporte**   | Transporte        | Asegura la llegada de los datos en orden y que sean completos. <br> - **TCP**: confiable pero lento (ideal para transferencia de archivos). <br> - **UDP**: no confiable pero rápido (ideal para multimedia en streaming). |
| **Capa Sesión**       | Aplicación        | Gestiona la comunicación entre dispositivos y mantiene activa la sesión. |
| **Capa Presentación** | Aplicación        | Se encarga de comprimir, cifrar y codificar los datos.                 |
| **Capa Aplicación**   | Aplicación        | Obtiene los datos directamente del usuario.                            |


## Cálculo de la Capacidad Teórica de los Enlaces Críticos Usando la Fórmula de Shannon

Para estimar la capacidad máxima de los enlaces más importantes de la red, se utilizó la fórmula de Shannon:

$$ C = B \cdot \log_2(1 + \text{SNR}) $$

Donde:

- **C** es la capacidad máxima del canal en bits por segundo (bps).
- **B** es el ancho de banda del canal (en este caso, 1 Gbps o \( 1 \times 10^9 \) bps, ya que todos los enlaces usan interfaces Gigabit).
- **SNR** es la relación señal a ruido en forma lineal (no en decibelios), estimada según la distancia del enlace.

A continuación se presentan los resultados calculados para cada enlace crítico identificado en la topología de red:



### Enlace entre el Switch central y los servidores (Servers-PT) ubicados en un búnker subterráneo a 30 metros

- **Distancia:** 30 metros
- **SNR estimado:** 3162.3 (equivalente a 35 dB)
- **Capacidad teórica:** 11.63 Gbps

### Enlace entre el Switch central y el Router de Secretaría

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (equivalente a 40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch central y el Router del Recinto

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch central y el Router de la Sala de Videoconferencia

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch central y el Router del Laboratorio

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch central y el Router Externo, que representa otro edificio a 3 km de distancia

- **Distancia:** 3 km
- **SNR estimado:** 316.2 (25 dB)
- **Capacidad teórica:** 8.31 Gbps

  
## Modulaciones

- **Gigabit Ethernet (1 Gbps)**: Se utiliza **PAM-5** porque permite una transmisión eficiente sobre cables de cobre utilizando 5 niveles de amplitud.
- **Fast Ethernet (100 Mbps)**: Se emplea **PAM-4** debido a que necesita 4 niveles de amplitud para transmitir a 100 Mbps de manera confiable.
- **Comunicaciones inalámbricas (Wi-Fi)**: Se usa **64-QAM** cuando las condiciones de la señal son óptimas, ya que ofrece una alta eficiencia espectral, permitiendo transmitir más bits por símbolo, pero adaptándose a condiciones variables de señal mediante modulación adaptativa.

