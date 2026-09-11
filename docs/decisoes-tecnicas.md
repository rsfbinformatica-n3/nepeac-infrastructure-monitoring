# Decisões técnicas

## Docker Compose

Escolhido por simplicidade, reprodutibilidade e baixo overhead para ambiente local pequeno.

## Acesso privado

Painéis administrativos devem ser acessados por rede privada/VPN mesh, evitando exposição pública direta.

## Inventário antes de CMDB pesada

A primeira fase usa JSON/CSV/Markdown e descoberta controlada, sem instalar GLPI, NetBox, OCS, Snipe-IT ou Wazuh.

## Wazuh

Avaliado como tecnologia útil, mas descartado neste host por limitação de RAM/CPU e necessidade de manter margem operacional para a stack existente.

## Sensor Wi-Fi

Um segundo adaptador Wi-Fi foi planejado para observabilidade passiva/controlada de SSIDs/BSSIDs, sem se tornar rota principal do servidor.
