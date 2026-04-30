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
    Co overflow hidden me aseguro que nada sobresalga.

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
        

    
