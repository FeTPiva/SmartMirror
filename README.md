# micro3obi

Materiais utilizados:

Raspberry pi3
display lcd 7"
vidro 15x9cm
insufilm g5 espelhado
infravermelho
sensor de umidade am2302
fita led rgb
cola quente
superbonder

Equipamentos:

impressora 3D
Furadeira

Instruções:

1-Moldura:
Imprima os arquivos Peça1, tampa e tras
Com a furadeira, faça os furos para o encaixe do infravermelho.

2-Espelho:
Utilizando água e sabão limpe o vidro e então com o insufilme cortado no tamanho adequado cole-o com cuidado para não fazer bolhas(utilize uma régua para evitar as bolhas)

4-Raspberry:
Utilize a instalação NOObs para o raspberry. Nele, visite o site https://magicmirror.builders/ e pelo cmd do linux execute o comando bash -c "$(curl -sL https://raw.githubusercontent.com/MichMich/MagicMirror/master/installers/raspberry.sh)" para fazer download e instalar o Magic Mirror.
No proprio site haverão vários possiveis módulos que poderão ser instalados. Para cada um deles deverá ser utilizado o comando npm install para que eles sejam instalados.

Feito isso, comece a configuração dos modulos no arquivo config, dentro da pasta config.

4.1 Clock
https://github.com/MichMich/MagicMirror/tree/master/modules/default/clock
config:



4.2 Calendar

