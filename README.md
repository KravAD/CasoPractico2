# CasoPractico2
Enlace Repositorio GitHub --> https://github.com/KravAD/CasoPractico2.git

# Modelado de la Comunicación (OSI/TCP-IP)

| Capa OSI             | Capa TCP/IP     | Función                                                                 |
|----------------------|------------------|-------------------------------------------------------------------------|
| **Capa Física**       | Acceso a red     | Transmite los datos por un medio físico.                               |
| **Capa Enlace de datos** | Acceso a red     | Controla el flujo de datos, detecta y corrige errores e identifica dispositivos mediante direcciones MAC. |
| **Capa Red**          | Acceso a red     | Usa direcciones IP y se encarga de direccionar y enrutar los paquetes de datos. |
| **Capa Transporte**   | Transporte        | Asegura la llegada de los datos en orden y que sean completos. <br> - **TCP**: confiable pero lento (ideal para transferencia de archivos). <br> - **UDP**: no confiable pero rápido (ideal para multimedia en streaming). |
| **Capa Sesión**       | Aplicación        | Gestiona la comunicación entre dispositivos y mantiene activa la sesión. |
| **Capa Presentación** | Aplicación        | Se encarga de comprimir, cifrar y codificar los datos.                 |
| **Capa Aplicación**   | Aplicación        | Obtiene los datos directamente del usuario.                            |

![image](https://github.com/user-attachments/assets/204f4fd1-a1bc-4a21-b58e-70776d1bdef6)

# Capa Física
## Cálculo de la Capacidad Teórica de los Enlaces Críticos Usando la Fórmula de Shannon

Para estimar la capacidad máxima de los enlaces más importantes de la red, se utilizó la fórmula de Shannon:

$$ C = B \cdot \log_2(1 + \text{SNR}) $$

Donde:

- **C** es la capacidad máxima del canal en bits por segundo (bps).
- **B** es el ancho de banda del canal (en este caso, 1 Gbps o \( 1 * 10^9 \) bps, ya que todos los enlaces usan interfaces Gigabit).
- **SNR** es la relación señal a ruido en forma lineal (no en decibelios), estimada según la distancia del enlace.

### Conversión de SNR de dB a Lineal

Para convertir la **Relación Señal a Ruido (SNR)** de **dB** a **forma lineal**, se utiliza la siguiente fórmula:

$$ SNR_{lineal} = 10^{\frac{\text{SNR}_{dB}}{10}} $$

A continuación se presentan los resultados calculados para cada enlace crítico identificado en la topología de red:



### Enlace entre el Switch central y los servidores (Servers-PT) ubicados en un búnker subterráneo a **1.5 km y 30 metros bajo tierra**

- **Distancia:** 1.5 km + 30 metros subterráneos  
- **SNR estimado:** 2630 (equivalente a 34.2 dB)  
- **Capacidad teórica:** 11.36 Gbps

### Enlace entre el Router Externo y los servidores (Servers-PT) ubicados en un búnker subterráneo a **1.5 km y 30 metros bajo tierra**

- **Distancia:** 1.5 km + 30 metros subterráneos  
- **SNR estimado:** 2630 (equivalente a 34.2 dB)  
- **Capacidad teórica:** 11.36 Gbps  

### Enlace entre el Switch Central y el Router de Secretaría

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (equivalente a 40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Central y el Router del Recinto

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Central y el Router de Zona Aulas

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps
- 
### Enlace entre el Switch Central y el Router de la Sala de Videoconferencia

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Central y el Router del Laboratorio

- **Distancia:** 200 metros
- **SNR estimado:** 10,000 (40 dB)
- **Capacidad teórica:** 13.29 Gbps

### Enlace entre el Switch Central y el Router Externo, que representa otro edificio a 3 km de distancia

- **Distancia:** 3 km
- **SNR estimado:** 316.2 (25 dB)
- **Capacidad teórica:** 8.31 Gbps

  
## Modulaciones

- **Gigabit Ethernet (1 Gbps)**: Se utiliza **PAM-5** porque permite una transmisión eficiente sobre cables de cobre utilizando 5 niveles de amplitud.
- **Fast Ethernet (100 Mbps)**: Se emplea **PAM-4** debido a que necesita 4 niveles de amplitud para transmitir a 100 Mbps de manera confiable.
- **Comunicaciones inalámbricas (Wi-Fi)**: Se usa **64-QAM** cuando las condiciones de la señal son óptimas, ya que ofrece una alta eficiencia espectral, permitiendo transmitir más bits por símbolo, pero adaptándose a condiciones variables de señal mediante modulación adaptativa.

# Capa de Red

### Subredes IPv6
| **Subred IPv6**       | **Rango de Hosts**                                      |
|-----------------------|--------------------------------------------------------|
| `2001:DB8:10::/64`    | `2001:DB8:10::1` - `2001:DB8:10:0:ffff:ffff:ffff:ffff` |
| `2001:DB8:20::/64`    | `2001:DB8:20::1` - `2001:DB8:20:0:ffff:ffff:ffff:ffff` |
| `2001:DB8:30::/64`    | `2001:DB8:30::1` - `2001:DB8:30:0:ffff:ffff:ffff:ffff` |
| `2001:DB8:40::/64`    | `2001:DB8:40::1` - `2001:DB8:40:0:ffff:ffff:ffff:ffff` |
| `2001:DB8:50::/64`    | `2001:DB8:50::1` - `2001:DB8:50:0:ffff:ffff:ffff:ffff` |

### Direcciones Multicast en IPv6
En IPv6 no existe el broadcast tradicional de IPv4. En su lugar, se utilizan direcciones multicast:
- **`ff02::1`**:  
  Equivalente al broadcast en IPv4. Se usa para comunicarse con **todos los dispositivos** en la subred.  
  Ejemplo: Descubrimiento de vecinos (*Neighbor Discovery*).

- **`ff02::2`**:  
  Reservado para la comunicación exclusiva entre **routers** en la subred.  
  Ejemplo: Intercambio de rutas en protocolos como OSPFv3.
  
- **Hosts por subred**: Cada subred `/64` permite hasta **2^64 hosts** (≈ 18 trillones de direcciones).
- **Formato de direcciones**: Los hosts válidos van desde `<prefijo>::1` hasta `<prefijo>:0:ffff:ffff:ffff:ffff`.

## Dijkstra
![Imagen de WhatsApp 2025-04-21 a las 23 03 07_5ec83c0c](https://github.com/user-attachments/assets/ec21ceef-efe7-4611-a800-eb7821e4f53c)

## Enrutamiento por inundación 
En nuestro proyecto, el enrutamiento por inundación puede utilizarse como mecanismo de respaldo si falla alguna ruta entre aulas, bibliotecas o laboratorios. Este método reenvía los paquetes por todas las rutas disponibles, asegurando que los datos lleguen aunque se caiga un enlace o router.

Aunque no es eficiente como sistema principal, resulta útil en situaciones de emergencia, ya que mantiene la comunicación activa mientras se restablece la ruta óptima. Con controles como TTL o identificación de paquetes, se evita la duplicación innecesaria. Es una forma de garantizar tolerancia a fallos en la red implementada.


#  Capa de Transporte

## Decisión de Protocolos
| **Protocolo** | **Aplicación**         | **Justificación**                                                                 |
|---------------|------------------------|-----------------------------------------------------------------------------------|
| **TCP**       | Transferencia de archivos (FTP/SFTP) | - **Orientado a conexión**: Garantiza entrega confiable mediante ACKs.<br>- **Control de congestión**: Adapta dinámicamente la tasa de transmisión.<br>- **Retransmisión de paquetes perdidos**: Ideal para integridad de datos. |
| **UDP**       | Streaming multimedia   | - **Sin conexión**: Minimiza sobrecarga y latencia.<br>- **Tolerancia a pérdidas**: Paquetes perdidos no afectan significativamente la experiencia.<br>- **Prioriza velocidad**: No espera confirmaciones. |

---

## Cálculo del Tamaño Óptimo de la Ventana TCP
#### **Parámetros Clave**
| **Variable**          | **Valor**               |
|-----------------------|-------------------------|
| MTU                   | 1500 bytes              |
| RTT (Round-Trip Time) | 12 ms (0.012 segundos)  |
| Ancho de Banda        | 1 Gbps (1,000,000,000 bits/segundo) |
| MSS (Maximum Segment Size) | 1460 bytes       |

El MTU, RTT y ancho de banda se han obtenido del pkt usando el comando "ping" y "show interfaces" .

Cálculo de Ventana TCP – Markdown

## Paso 1: Calcular el MSS

math
\text{MSS} = \text{MTU} - \text{Encabezados IP/TCP} = 1500\,\text{bytes} - 40\,\text{bytes} = 1460\,\text{bytes}


---

## Paso 2: Calcular el Bandwidth-Delay Product (BDP)

math
\text{BDP (bits)} = \text{Ancho de Banda} \times \text{RTT} = 1,000,000,000\,\text{bits/s} \times 0.012\,\text{s} = 12,000,000\,\text{bits}


math
\text{BDP (bytes)} = \frac{12,000,000\,\text{bits}}{8} = 1,500,000\,\text{bytes}


---

## Paso 3: Determinar el Tamaño de la Ventana TCP

math
\text{Ventana Óptima (bytes)} = \text{BDP} = 1,500,000\,\text{bytes}


math
\text{Ventana Óptima (segmentos)} = \frac{\text{BDP}}{\text{MSS}} = \frac{1,500,000\,\text{bytes}}{1460\,\text{bytes/segmento}} \approx 1027\,\text{segmentos}


---

## Influencia en la Eficiencia de Transmisión

### Ventana = BDP:
- Eficiencia del *100%*: Mantiene el enlace saturado sin subutilización.
- Evita congestión: La ventana no excede la capacidad de la red.

### Ventana < BDP:
- *Subutilización*: El enlace no se aprovecha completamente, reduciendo el rendimiento.

### Ventana > BDP:
- *Congestión*: Satura el búfer de los routers, causando pérdida de paquetes y retransmisiones.



