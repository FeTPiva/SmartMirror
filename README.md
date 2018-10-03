# micro3obi

Materiais utilizados:

Raspberry pi3 <br>
display lcd 7"<br>
vidro 15x9cm<br>
insufilm g5 espelhado<br>
infravermelho<br>
sensor de umidade am2302<br>
fita led rgb<br>
cola quente<br>
superbonder<br>

Equipamentos:

impressora 3D<br>
Furadeira<br>

Instruções:

1-Moldura:

Imprima os arquivos Peça1, tampa e tras<br>
Com a furadeira, faça os furos para o encaixe do infravermelho.<br>

2-Espelho:

Utilizando água e sabão limpe o vidro e então com o insufilme cortado no tamanho adequado cole-o com cuidado para não fazer bolhas(utilize uma régua para evitar as bolhas)

4-Raspberry:

Utilize a instalação NOObs para o raspberry. Nele, visite o site:
https://magicmirror.builders/ e pelo cmd do linux execute o comando bash -c "$(curl -sL https://raw.githubusercontent.com/MichMich/MagicMirror/master/installers/raspberry.sh)" 
para fazer download e instalar o Magic Mirror.
No proprio site haverão vários possiveis módulos que poderão ser instalados. Para cada um deles deverá ser utilizado o comando npm install para que eles sejam instalados.

Modulos utilizados:

    4.1 Clock

    https://github.com/MichMich/MagicMirror/tree/master/modules/default/clock
    config:


    4.2 Calendar

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

    4.3 Compliments



    4.4 CurrentWeather

    {
			module: "currentweather",
			position: "top_right",
			config: {
				location: "Sao Paulo",
				locationID: "",  //ID from http://www.openweathermap.org/help/city_list.txt
				appid: "YOUR_OPENWEATHER_API_KEY"
			}
		},
        
        4.5 Weather Forescast

    {
			module: "weatherforecast",
			position: "top_right",
			header: "Weather Forecast",
			config: {
				location: "Sao Paulo,Brasil",
				locationID: "3448439",  //ID from http://www.openweathermap.org/help/city_list.txt
				appid: "f9023beccf412c403c13c2f5970b020c"
			}
		},
        
        4.6 News

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
        
        4.7


