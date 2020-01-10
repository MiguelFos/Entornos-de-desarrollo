Primer To-Do

1-He compilat l'arxiu hola.c i he obtés l'arxiu a.out . (gcc hola.c)
2-Per a donar-li el nom hola he compilat utilitzant gcc hola.c -o hola .
3-He utilitzat gcc -Wall -g hola.c -o hola , on -Wall i -g serveixen per a mostrar els warnings durant la compilació .
4-He comprobat que al utilitzar make hola aconseguisc el mateix efecte que al punt 2. Crea l'executable hola i sobreenten que el fitxer font es hola.c .

Segon To-Do

1-Cree i compile mitjançant gcc calc.c -o calcula i despres l'he executat amb ./calcula. He comprobat que funciona.
2-He anyadit les linees:
int major(int op1, int op2) {
	if(op1>op2){
	return op1;
	}
	if(op2 > op1){
	return op2;
	}else{
        return 0;
    }

i també al main 

printf("El major entre %d y %d es %d\n",a,b,major(a,b));

3- He creat i compilat gcc calc.c -o calcula i despres executat ./calcula. També funciona.
4- Cree l'arxiu calc.h, el cual conté les capçaleres. També crearem l'arxiu calc.c on tindrem sols les funcions. A l'arxiu calcula. c tindrem el main.
5- Obtenim el fitxer objecte calc.o mitjançant gcc -c calc.c -o calc.o .
6- Per a obtenir el fitxer executable calcula farem gcc calc.o calcula.c -o calcula . Dins de l'arxiu calcula.c tindrem que tindre #include "calc.h".
7-Una volta obtés calcula, l'executarem. ./calcula . També funciona.

tercer To-Do

1- Creem el makefile.
2- Amb make crea els arxius calc.o y calcula. Açó ho fa per que amb make executa la primera regla. Com necesita crear calc.o per a realitzar la primera regla, també creara calc.o . En cas de no haver necesitat crear calc.o , sols hauria realitzar la primera.
3- Amb make calcula pasará el mateix, ja que per a realitzar la regla calcula, necesita de calc.o , encara que en este cas, executará calcula xq li ho hem demanat directament, no per que siga la primera regla.
4- Amb make calc, sols obtindrem l'arxiu calc.o .
5- Invertim les regles a makefile i al fer make, sols ens creara calc.o, degut a que sols realitza la primera regla. Com no necesita de cap altra per a complirse, será la unica realitzada.
6- Retornem les regles al seu lloc.

Comprobació de targets

1- Calcula

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make calcula
gcc -Wall -g -c calc.c -o calc.o

2-calc.o

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make calc
gcc -Wall -g -c calc.c -o calc.o
gcc   calc.o   -o calc


3-Clean

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make clean
rm -rf *.o
rm calcula

4-Dist

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make dist
rm -rf ../dist;
mkdir -p ../dist/usr/bin/calc
cp calcula ../dist/usr/bin/calc

5-Targz

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make targz
mkdir -p source
cp *.c *.h Makefile source
tar -cvfcalcula.tar source
source/
source/calc.c
source/calc.h
source/calcula.c
source/Makefile
gzip calcula.tar
rm -rf calcula.tar
rm -rf source

6-Install

xubuntu@xubuntu-VirtualBox:~/GitHub/Entornos-de-desarrollo/Unitat4/Make$ make install
rm -rf ../dist;
mkdir -p ../dist/usr/bin/calc
cp calcula ../dist/usr/bin/calc
cp -r ../dist/* /
cp: no se puede crear el directorio '/usr/bin/calc': Permiso denegado
Makefile:32: recipe for target 'install' failed
make: *** [install] Error 1


En el cas de install entenc que el problema es que no tinc permis per a copiar un arxiu a la arrel. 