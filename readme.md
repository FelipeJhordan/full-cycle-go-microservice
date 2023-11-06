## Microserviço para processamento e conversão de formato de vídeo

## Fluxo
- Recebe uma mensagem via RabbitMQ informando qual vídeo deve ser convertido
- Faz download do vídeo no Google Cloud Storage
- Fragementa O vídeo
- Converte o Vídeo para MPEG-DASH
- Faz o upload do vídeo no Google Cloud Storage
- Envia uma notificação via fila com as informações do vídeo convertido ou informando erro na conversão
- Em caso de erro, a mensagem original enviada via RabbitMQ será rejeitada e encaminhada diretamente a uma Dead Letter Exchange.