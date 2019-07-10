<a href="http://mcm.ipg.pt"><img src="http://www.ipg.pt/website/imgs/logotipo_ipg.jpg" title="IPG(MCM)" alt="IPG MCM 2018/19"></a>

# The Things Network collaborative sensor maps

Os dados ficam muito mais bonitos quando os pode visualizar. Este projeto torna fácil mostrar dados de sensores de nodes LoRaWAN conectados à rede Things num mapa. Porque todos podem adicionar os seus sensores fornecendo apenas uma chave API, é muito útil para trabalhos ou apresentações do LoRaWAN. Os mapas funcionam em desktop e móvel, e os dados são automaticamente sincronizados entre os clientes.

# Como instalar

1. Clonar este repositório:

    ``
      $git clone https://github.com/daeynasvistas/LoRa-TTN-map
    ``

1. Instalar as dependências:

    ``
    $ npm install
    ``

1. Executar o servidor:

    ``
     node server.js
    ``

1. Navegar para http://localhost:3000.


** Google Maps API Key**

Antes de implantar esta aplicação, vai precisar da sua própria chave API Maps. Ir para [esta página web] (https://developers.google.com/maps/documentation/javascript/get-api-key) e obter um. Então abra o servidor.js e introduza a API no objecto "config".

## Adicionando dados ao mapa

1. Vá à sua consola da rede Things N. e anote o ID de Aplicação.
1. Na parte inferior dessa página existe uma 'chave de Aplicação'. Anotar também.
1. Volte para a aplicação e indique o seu ID da aplicação no campo de texto do canto superior direito.
1. Quando solicitado, introduza a sua chave da aplicação.
1. Os dados agora aparecem automaticamente no mapa.

Pode adicionar muitas aplicações desta forma, o que é ótimo para mostrar multiplos nodes.
Para remover uma aplicação, procure em "db.json" e remova a entrada de lá.

## Configuração

Para configurar os dados que são mostrados, abra o server.js. Aqui tens o objecto "config". É aqui que especifica quais gráficos precisam ser mostrados e como os dados precisam ser mapeados.

Objetos são colocados automaticamente perto do centro do mapa, e podem ser arrastados para a sua localização real. Para mudar o nível de zoom, procure em "public/maps.js". Se um dispositivo tem GPS, pode anular este comportamento e usar as coordenadas reais, definindo as propriedades  "lat" e  "lng" de um dispositivo em "server.js". Certifique-se que emite um evento "location-change" para que todos os clientes possam ver o novo local.

Os gráficos podem ser configurados no objeto "config" em "public/maps.js". Ex. para permitir que mais gráficos sejam exibidos, pode desativar as os eixos x e de seguida, baixar a altura da área de desenho. Este projecto utiliza [Chart.js](http://www.chartjs.org/).


## Resultado
![mcm_ttn](https://user-images.githubusercontent.com/2634610/60970403-cec46c80-a319-11e9-9eca-e0ffad3d28e0.PNG)

