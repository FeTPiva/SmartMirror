# Smart Mirror v1

O trabalho do terceiro bimestre de microcoontroladores teve por objetivo utilizar o microcomputador Raspberry Pi 3 e o GPIO (general-purpose input/output), que é responsável por fazer a comunicação de entradas e saídas de sinais digitais, em seu funcionamento. 
O projeto desenvolvido foi um espelho inteligente. Esse espelho além de refletir a imagem auxilia no dia-a-dia de uma pessoa.
Nele é possível interagir diretamente com o usuário através do sensor infravermelho que detecta movimentação próxima ao espelho e ativa a tela de LCD(ou leds) que está através desse espelho.
Essa tela pode ser controlada através do WiFi pelo celular, se utilizando do ip do raspberry e mostrará o horário atual, a temperatura ambiente,previsão do tempo, frases do dia, notícias, calendário de feriados e um organizador de tarefas (Trello).

<h2>Materiais utilizados:</h2>

Raspberry pi3 <br>
display lcd 7"<br>
vidro 15x9cm<br>
insufilm g5 espelhado<br>
infravermelho<br>
sensor de umidade am2302<br>
fita led rgb<br>
cola quente<br>
superbonder<br>

<h2>Equipamentos:</h2>

impressora 3D<br>
Furadeira<br>

<h2>Instruções:</h2>

<h3>1-Moldura:</h3>

Imprima os arquivos Peça1, tampa e tras na impressora 3D.
Preferencialmente utilize algum material de cor preta
Com a furadeira, faça os furos para o encaixe do infravermelho onde achar mais conveniente.

<h3>2-Espelho:</h3>

Utilizando água e sabão limpe muito bem o vidro e então com ele seco e o insufilme cortado no tamanho adequado,
cole-o com cuidado para não fazer bolhas(utilize uma régua para evitar as bolhas)

<h3>3-Raspberry:</h3>

Utilize a instalação NOOBs para o raspberry. Nele, visite o site:
https://magicmirror.builders/ e pelo cmd do linux execute o comando bash -c "$(curl -sL https://raw.githubusercontent.com/MichMich/MagicMirror/master/installers/raspberry.sh)" 
para fazer download e instalar o Magic Mirror.
dica para download de forma rápida:
comando no cmd 'git clone urlDoGit.git '
No proprio site haverão vários possiveis módulos que poderão ser instalados. Para cada um deles deverá ser utilizado o comando npm install para que eles sejam instalados. 
Após isso é preciso realizar o setup de cada um no arquivo config.js na pasta config. Abaixo os módulos utilizados c suas respectivas configurações a serem adicionadas no arquivo config.js


<h3>Modulos utilizados:</h3>

   <h4>3.1 Trello</h4>
    https://github.com/Jopyth/MMM-Trello
	
	{
        module: 'MMM-Trello',
        position: 'bottom_center', // This can be any of the regions, best results in center regions.
        config: {
            // See 'Configuration options' for more information.
            api_key: "INSERT_YOUR_API_KEY",
            token: "INSERT_YOUR_TOKEN",
            list: "INSERT_YOUR_LIST_ID"
        }
    },

   <h4>3.2 Calendar</h4>
	já vem com o magic mirror padrão

    {
		module: "calendar",
		header: "US Holidays",
		position: "top_left",
		config: {
			calendars: [
				{
					symbol: "calendar-check-o ",
					url: "webcal://www.calendarlabs.com/templates/ical/US-Holidays.ics"
				}
			]
		}
	},

	neste modulo pode ser alterado o site chamado na url para algum de preferencia.

   <h4>3.3 Controle infravermelho</h4>
	https://github.com/paviro/MMM-PIR-Sensor


	{
		module: 'MMM-PIR-Sensor',
		config: {
			powerSavingDelay: 10
			}
	},

	Neste foi utilizado o pino 21 para controle do sensor

   <h4>3.4 CurrentWeather</h4>
	já vem com o magic mirror padrão

    {
		module: "currentweather",
		position: "top_right",
		config: {
			location: "Sao Paulo",
			locationID: "",  //ID from http://www.openweathermap.org/help/city_list.txt
			appid: "YOUR_OPENWEATHER_API_KEY"
		}
	},
        
   <h4>3.5 Weather Forescast</h4>
	já vem com o magic mirror padrão

    {
		module: "weatherforecast",
		position: "top_right",
		header: "Weather Forecast",
		config: {
			location: "Sao Paulo,Brasil",
			locationID: "3448439",  //ID from http://www.openweathermap.org/help/city_list.txt
			appid: "ADIQUIRIR_FREE_kEY_NO_SITE_ACIMA"
		}
	},
        
   <h4>3.6 News</h4>
	já vem com o magic mirror padrão

    {
		module: "newsfeed",
		position: "bottom_bar",
		config: {
			feeds: [
				{
					title: "Sao Paulo",
					url: "http://www.nytimes.com/services/xml/rss/nyt/HomePage.xml"
				}
			],
			showSourceTitle: true,
			showPublishDate: true
		}
	},
        
  <h4>3.7 IP Na tela</h4>
	   recurso muito útil para a utilização mais facil do modulo de remote control.

	   https://github.com/fewieden/MMM-ip
	   {
    	module: 'MMM-ip',
    	position: 'bottom_right',
    	config: {
			showFamily:'IPv4' //se for wifi sendo utilizado
			//usar 'eth0' se for conexão por cabo
       
    		}
		}


   <h4>3.8 Remote Control</h4>
	   Este módulo é muito importante e útil no projeto.
	   Através dele é possivel controlar todos os módulos sendo exibidos na tela do magic mirror. basta usar o link  http://www.xxx.y.zzz:8080/remote.html onde w, x, y e z formarão o ip sendo mostrado na tela do magic mirror.
	   Vale lembrar que o raspberry e o dispositivo acessando o link DEVEM estar na mesma rede.

	   download: https://github.com/Jopyth/MMM-Remote-Control

	   acima da tag "mudules[ ...resto do codigo..." deve haver o seguinte setup:
	   address: "0.0.0.0", // Address to listen on, can be:
	                      // - "localhost", "127.0.0.1", "::1" to listen on loopback interface
	                      // - another specific IPv4/6 to listen on a specific interface
	                      // - "", "0.0.0.0", "::" to listen on any interface
	                      // Default, when address config is left out, is "localhost"
		port: 8080,
		ipWhitelist: [], // Set [] to allow all IP addresses
	                     // or add a specific IPv4 of 192.168.1.5 :
	                     // ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.1.5"],
	                     // or IPv4 range of 192.168.3.0 --> 192.168.3.15 use CIDR format :
	                     // ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:192.168.3.0/28"],

		language: "en",
		timeFormat: 24,
		units: "metric",

   <h4>3.9 Traffic</h4>
		tempo gasto indo de um lugar ao outro

		https://github.com/SamLewis0602/MMM-Traffic

		{
			module: 'MMM-Traffic',
			position: 'top_left',
			//classes: 'dimmed medium', optional, default is 'bright medium', only applies to commute info not route_name
			config: {
				api_key: 'API_DO_GOOGLEMAPS',
				mode: 'driving',
				origin: 'Av Paulista ...',
				destination: 'Praca Maua 1, Sao Caetano do Sul, SP',
				//mon_destination: '116th St & Broadway, New York, NY 10027',
				//fri_destination: '1 E 161st St, Bronx, NY 10451',
				//arrival_time: '0800', //optional, but needs to be in 24 hour time if used.
				route_name: 'Trabalho Para Faculdade',
				changeColor: true,
				showGreen: false,
				limitYellow: 5, //Greater than 5% of journey time due to traffic
				limitRed: 20, //Greater than 20% of journey time due to traffic
				traffic_model: 'optimistic',
				interval: 1200000 //2 minutes
				}
		},

   <h4>3.10 Local Temperature</h4>
		https://github.com/glitch452/MMM-LocalTemperature

		{
            module: "MMM-LocalTemperature",
            position: "right", // Only add a position if you want this module to display the data
            header: "Temperatura",
            config: {
            sensorPin: 22, // For GPIO 22
            }
          }, 
		{
		
		Neste há um setup extra. Para habilitar a leitura de temperatura/úmidade é preciso ir na pasta do módulo e editar seu arquivo de mesmo nome.js.
		Lá alterar os campos de sensorPin, showTemperature, showHumidity,temperatureText e humidityText para TRUE


Créditos: Fernanda T. Piva, Adriana Padilla e Nicolas Umaras





	



