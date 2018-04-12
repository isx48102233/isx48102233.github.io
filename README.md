# Documentació pàgina web M09. Adrián Dávila Montañez.

## Creació del repositori
En primer lloc procedim amb la creació d'un repositori a GitHub fent login al teu usuari i visitant <https://github.com/new> per a la creació d'un nou repositori utilitzat per al projecte. L'anomenarem com vulgem pero serà el nom que desprès s'utilitzarà per accedir-hi. En el meu cas es [isx48102233.github.io](https://github.com/isx48102233/isx48102233.github.io).

**Important:** Aquest repositori ha de ser **Públic**

## Treball en local
Per a una bona pràctica, afegirem un remote a la nostra màquina, per a treballar localment i així afegir fitxers com imatges, pdfs, etc..

    mkdir isx48102233.github.io
    cd isx48102233.github.io/
    git pull git@github.com:isx48102233/isx48102233.github.io.git
    git remote add projecte git@github.com:isx48102233/isx48102233.github.io.git
Així doncs quan volguem que un canvi sigui oficial farem:
    
    git add .
    git commit -am "Descripcio del commit"
    git push projecte master
    
## Organització del repositori
En aquest punt pensem en l'organització del repositori. On volem tenir les imatges? On volem tenir les pàgines html? Volem fer plantilles?

En el meu cas ho explico a continuació:
 * Carpetes per a cada secció de la web, carpeta per a css, carpeta per a imatges i carpeta per a multimedia(video).
 * Index de cada secció a la seva carpeta, amb plantilla allotjada a la carpeta **\_layout**.
 * Documents pertanyents a una secció allotjats a la carpeta de la secció (pdfs).

## Creació de plantilles

Utilitzarem una platilla per a les pàgines de la web. Es una plantilla anomenada default.html allotjada a la carpeta **\_layout**. En aquesta plantilla el que farem es incorporar el **\<head>** (on hi serà el **main.css**), el **\<body>** amb la **barra de navegació** i el **\<footer>**.

### HEAD
        <head>
            <title>{{ page.title }}</title>
            <!-- link to main stylesheet -->
            <link rel="stylesheet" type="text/css" href="/css/main.css">
            <link href='https://fonts.googleapis.com/css?family=Bangers' rel='stylesheet'>
        </head>
### BODY
        <body>
            <nav>
                <ul>
                    <li><a href="/">Pàgina d'inici</a></li>
                    <li><a href="/personal">Informació personal</a></li>
                    <li><a href="/experiencia">Experiència laboral</a></li>
                </ul>
            </nav>
### FOOTER
        <footer>
            <a target="_blank" href="mailto:adridavila1997@gmail.com"><img class="footer_img"src=/images/gmail.png></a>
            <a target="_blank" href="https://github.com/isx48102233"><img class="footer_img" src=/images/github.png></a>
            <a target="_blank" href="https://gitlab.com/isx48102233"><img class="footer_img" src=/images/gitlab.png></a>
            <a target="_blank" href="https://www.twitter.com/xdri97"><img class="footer_img" src=/images/twitter.png></a>
            <a target="_blank" href="https://www.instagram.com/xdri97"><img class="footer_img" src=/images/insta.png></a>
        </footer>
        </body>
### CONTINGUT
La clau per al contigut es ficar-hi, entre la **barra de navegació** i el **footer** el que desprès serà substituit a cada pàgina, es a dir:

        <div class="container">
            {{ content }}
        </div>
        
Amb això, i substituint a cada index de cada pàgina amb el propi contingut tindrem el sistema de platilles; **layout** es la carpeta de plantilles i **default** el nom de la plantilla. Title substituirà a la part de **head** per a donar nom a la pàgina:
       
        ---
        layout: default
        title: Pàgina d'inici
        ---
        
## Inserció de contingut        
### Pàgina d'inici
Aquesta pàgina es molt senzilla. Consta de:
1. Plantilla amb Head, Navbar i footer

        ---
        layout: default
        title: Pàgina d'inici
        ---
2. Títol
        
        <h1>Benvinguts a la meva web!</h1>
3. Text d'introducció
        
        <p>Presento la meva web feta bàsicament amb GitHub Pages per al M09 del cicle formatiu de grau superior d'ASIX (Administració de Sistemes i Xarxes) a l'Escola del Treball de Barcelona (EDT) durant el curs 2017-2018.</p>
4. Link a info personal

        <p>Si vols saber una mica més sobre mi... <a href="/personal">CLICK!</a></p>
5. Imatge de portada

        <img src=/images/portada.jpg width=100%>
        
### Personal
Bàsicament conté el mateix que l'inici pero afegim una imatge abans de les linies.

        <li><img src=/images/tick.svg width=15px height=15px> Centre: Institut Anna Gironella de Mundet</li>

També afegeixo un video (disponible amb Chrome).

        <div class=video>
            <video width="800" height="480" controls>
            <source src="/multimedia/xdri97.mp4" type="video/mp4">
            Your browser does not support the video tag.
            </video>
        </div>
### Experiencia
D'aquesta pàgina resaltar l'introducció dels CV en pdf mitjançant unes banderes a la part superior dreta:

        <a class=bancv target=_blank href=/cv/cvadridavilaesp.pdf><img class=flag src=/images/esp.png>&nbsp;</a><a class=bancv target=_blank href=/cv/cvadridavilacat.pdf><img class=flag src=/images/cat.png></a>

## Edició de css
Tot el css incorporat a la plantilla es a la carpeta **css** a l'archiu **main.css**.
### Barra de navegació i peu de pàgina
Per a la barra de navegació / peu de pàgina he fet varis canvis importants a css d'on destacaria:
* Llista sense style
* Cantonades amb cercle
* Display: inline-block
* Text alinieat al centre
        
        nav ul, footer {
        list-style: none;
        list-style-type: none;
        overflow: hidden;
        border-radius: 20px 20px 20px 20px;
        }
        
        nav ul li, footer ul li {
        display: inline-block;
        text-align: center;
        float: left;
}
### Hover
De no ser per aquest atribut, no sabriem mai quan i on hi ha un enllaç, per tant veig important destacar:
* Canvi de cursor
* Color diferent
        
        nav ul li a:hover {
        cursor: pointer;
        background-color: #87CEFA;
        }
        
### Font
Per a incorporar una font *no oficial* oferida per Google hem d'incorporar el css corresponent dins del **Head** dels documents on s'utilitza. En aquest cas la font s'utilitza a totes ja que pertany a la barra de navegació, present a cadascuna de les pàgines:
* Plantilla:
        
        <link href='https://fonts.googleapis.com/css?family=Bangers' rel='stylesheet'>
* CSS:
    * Barra de navegació i peu de pàgina:
    
            nav ul, footer {
            font-family: 'Bangers';
            }
    * Títols:        
        
            h1, h2, h3, h4{
            font-family: 'Bangers';
            color: #20B2AA;
            }

Fins aquí la meva pàgina web. Espero que us agradi i si teniu qualsevol *feedback* podeu contactar amb mi:

[ACCEDEIX (Recomenat amb Google Chrome)](https://isx48102233.github.io/)
