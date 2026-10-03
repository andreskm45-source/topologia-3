# topologia-3

Infraestructura 3: Acceso Remoto y Publicación de Servicios (Client-to-Site)

https://itlaedudo-my.sharepoint.com/:v:/g/personal/20250784_itla_edu_do/IQALD48iSZyqQYUUQ-0_hTrOAZ33fL-yke2LcYGsWqsrblI?e=EELTnT&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

Esta topología implementa un modelo de acceso de cliente (Client-to-Site) adaptado para el trabajo remoto. El router Cisco actúa exclusivamente como puerta de enlace a Internet para los usuarios mediante NAT puro, sin configuraciones criptográficas. El FortiGate asume un rol dual: opera como servidor VPN Dial-up (mediante FortiClient) para asegurar el acceso administrativo interno, y publica el servidor web hacia Internet utilizando una IP Virtual (Port Forwarding)[cite: 47]]

Parámetros de Red y ServiciosComponenteSubred / IPRol y ConfiguraciónUsuario (Cliente Remoto)10.7.84.0/25VLAN 10 (con DHCP). Sale a Internet mediante NAT Overload en el router Cisco.Servidor Web y SSH10.7.84.128/28Puerto físico dedicado detrás del FortiGate (IP: 10.7.84.130).Publicación Web (Virtual IP)IP Pública WANMapeo de puerto (Port Forwarding) del puerto externo 443 hacia el puerto interno 443 de la IP 10.7.84.130.VPN Remote AccessIP Pública WANTúnel IPsec configurado para FortiClient. 
Autenticación por Pre-Shared Key y grupo de usuarios locales.

Validaciones Realizadas
✅ Acceso Público (Sin VPN): Comprobación de navegación exitosa por HTTPS hacia la IP pública del FortiGate, permitiendo a cualquier usuario cargar la página web a través de la Virtual IP (VIP).
✅ Traceroute (Navegación Pública): Evidencia mediante tracepath de que el tráfico web fluye a través de la pasarela del Cisco (10.7.84.1) hacia el ISP, sin exponer la red privada del servidor.
✅ Bloqueo Administrativo Externo: Demostración de intentos de conexión SSH fallidos (Connection Refused/Timeout) al intentar acceder al servidor directamente desde Internet sin el túnel activo.

<img width="1005" height="586" alt="image" src="https://github.com/user-attachments/assets/bbeab1e3-f3fa-42a7-b109-7ba239799bb8" />
<img width="939" height="800" alt="image" src="https://github.com/user-attachments/assets/9848a759-5cb1-4a18-9f20-bef3bc67f30b" />
