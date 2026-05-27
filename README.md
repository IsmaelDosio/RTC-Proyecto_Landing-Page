HEADER
En un principio quise unsar tres elementos separados, aunque en el figma parece que el padre de todos es el nav. Yo los voy a mantener separados:
    - a para el logo
    - nav con una ul y 4 li para los enlaces de navegacion 
    - div para los botones de accion
Creo que asi tiene más sentido semántico.

Pero me resultaba muy dificil alinear el logo con el nav, tal y como aparece en el figma, asi que cambie la estrategia y uni en un mismo padre, en un div, el logo + nav. De esta manera con flex y align-items: center consegui el mismo resultado visual. 

Para los links del Nav use en CSS la propiedad inline-flex. Para tener el comportamiento de flex, para usar align-items:center, pero que el elemento solamente ocupe el espacio que necesite.

MAIN
Dentro del main meto las diferentes secciones
Sección 1: HERO
    Un contenedor para la img y un div para el texto que acompaña a la imagen. 
    Para meter el texto dentro de la imagen, usamos position relative y absolute. 
    Le ponemos relative al contenedor padre: class="hero" y relative al div class="hero-content" y despues colocamos el texto usando top y left.

    Use en el CSS tambien object-fit: cover para que la imagen cubra todo el espacio sin llegar a deformarse.

Sección 2 bloque con las tarjetas, 
    Para el HTML, a nivel semantico utilice una section para contener todo el bloque, y para las tarjetas utilicé artículos, cada uno por si mismo tienen sentido, por eso utilice esta etiqueta. 
    Cada Tarjeta lleva un 
        h2 + p + img + un footer con el boton de mas info y para mostrar los colores use la etiqueta span
    Para esta bloque, he usado grid, me pareció mas facil de usar grid aqui que flex. Para que la imagen se viera bien dentro del contenedor utilice object-fit: contain; y la decision de usar un div para el footer de la tarjeta es para darle flex y space between, asi el boton y los colores disponibles quedan en una posicion correcta

Sección 3: use de nuevo section, simplemente  con un H2 y un p. Para darles estilos use una clase y selectores para H2 y p

Seccion 4: 
    La lógica es la misma que en el hero:
    EL contenedor padre tiene position: relative.
    La imagen ocupa todo el bloque.
    .store-card tiene position: absolute.
    Con top y left, colocamos la caja encima de la imagen. Aunque aqui La diferencia es la caja en la que va el texto, ya que lleva un background diferente.
    Para que la imagen probe con object fit: cover, pero se deformaba, asi cambie a contain, y aun asi, no quedaba bien del todo, puse height en auto y asi al mantener la proporcion real, consegui el efecto correcto
    Para el HTML, de nuevo uso una seccion con la img y luego un div para contener la caja del texto, con un H2 y un a como enlace. Para que cuando cliques en el enlace, se abriese una pagina nueva, encontre la etiqueta target="_blank"
    He tenido que hacer una coreccion en esta seccion, porque al meter la siguiente seccion, esta se superponia en al siguiente, parece que con el css que tenia, le habia puesto a la class store.section un height fijo de 420px y al store-img un height: auto. Por lo que la imagen se hacia mas alta que el propio contenedor. Por lo que al quitar la altura fija del contenedor dejamos que sea la imagen la que mande en cuanto a la altura.
    Con overflow hidden me aseguro que nada sobresalga.
Seccion 6: 
    Aqui tenemos de nuevo una imagen grande que ocupa todo el ancho, y una caja de texto encima, en la parte inferior izquierda. Para posicionarlos uso de nuevo position relative y absolute para poner la caja de texto encima de la imagen y 
Seccion 7
    Esta seccion cambia, ahora tenemos dos columnas del mismo tamaño. A la izquierda el texto y a a la derecha la imagen. Dado que son dos columnas, utilizo de nuevo Grid, y le doy el mismo tamaño a las columnas, de 1fr 
Finalmente para el FOOTER: 
    Tenemos: 
        Una primera seccion con un background gris y un texto + boton, para posicionarlos uso grid con jsutify content: space-between para separarlos por igual dentro de la caja
        La zona central con la newsletter + data protection:
            Aqui para que tanto el checkbox como el texto fuera todo clicable, va el input dentro del label, hice las dos opciones, todo clicable y solo checkbox clicable, pero al final me gusto mas esta opcion, y aprendi esta forma de hacerlo, y tambien es mas facil para el css tener todo dentro y darle una class. Asi con flex y justify content center, queda perfectamente alineado.
        Uso de nuevo position relative y absolute para posicionar el boton de volver arriba de la pagina
        

    
CORRECCIONES: 

    1.Espacios en las imagenes: 
        Corregidos los espacios en los nombres de carpetas y de las imagenes: 
            1. Cars section --> Cars-section
                Corrigo igualmente cada una de las imagenes, con guion. 
            2. Tambien encontré la carpeta links RRSS, y la cambie a links-RRSS. 
    
    2. ARIA-LABEL en <section class="cars-section">
        Gracias, cuando lo use, estaba pensando en accesibilidad, pero no cai en que usandolo asi con un div, no tenia sentido, ya que un div semanticamente no significa nada, por lo que el ARIA-LABEL no ayuda. 
        He encontrado dos soluciones: 
            1. Tu sugerencia de añadir role
            Podria añadir role:list para car-colors y role:listitem para cada color, y de esta manera ya le estamos diciendo al navegador y por tanto al lector, que este elemento es una lista, y lo que es cada elemento de la lista. 

            2. Tambien vi la posibilidad de cambiar la etiqueta div, por una que tenga ya significado semantico por si misma, y que sea mas limpio, menos codigo y lo único que habria que añadir una atributo mas en el CSS. Y es cambiar div por UL y li.

            He optado por esta segunda opcion. Espero que resulte correcta, en mi cabeza despues de que lo hayas puntualizado tiene todo el sentido, y de paso me ha quedado mucho más claro el concepto de ARIA-LABEL. 

    3. Uso incorrecto de target:_blank
            1. En cars-section dado que son enlaces internos, el usuario sigue en la misma pestaña por lo que quito target:_blank de aqui y dejo para esta demo el href con #modelo correspondiente. 
            
            2. Añado este atributo en section class="categories", porque aqui, al ser un enlace externo, se abrira en una pestaña nueva 
    
    4. Checkbox fuera del form: 
            Es cierto, tal y como lo tengo el formulario estaria enviando la informacion de la subscripcion con el email pero no el ok a la politica de privacidad, por lo que no podriamos validar internamente si el usuario da su consentimiento o no.

            Para corregirlo, meto el checkbox dentro del form, pero ahora necesito separar el input del checkbox, asi que hago un div con una clase para el input y dejo el checkbox como lo tenia. 
            Tengo que ajustar el CSS
                Al quitarle flex a newsletter form, ya se comportan como dos bloques normales, uno debajo de otro. Y seguimos usando flex en cada uno de los dos bloques para colocar bien los elementos.

    5. RESPONSIVE: 

        Para que me sea más facil a la hora de revisar, voy a poner todas las medias queries al final del CSS en lugar de agruparlas cerca del CSS de la seccion que aplique en cada caso. De esta manera tengo el CSS desktop y CSS móvil

        Header hamburguesa.
            Empiezo atacando este bloque: el objetivo es ocultar el menú normal para que aparezca un botón hamburguesa.

            Para esto en el HTML añado un checkbox, que en escritorio estara oculto, y sera el CSS el que sepa si esta marcado o no. 
            El punto de corte lo pongo en 750px, a partir de ahi, mostramos el menu hamburguesa. 

            Cuando llegamos al puto de corte, ocultamos el menu navegacion con display: none y pasamos a mostrar la hamburguesa.

            Para el desplegable en el modo responsive, uso:   
            .menu-toggle:checked ~ .navegacion {
            display: block;
            }
            Cuando el checkbox esta marcado, entonces busca a su hermano que venga despues en el HTML y lo muestra. Y se marca cuando hacemos clic en el menu hamburguesa

        Hero móvil.
        Cards de coches.
        Red banner.
        Comprobación final de scroll horizontal.
        

