<div align="center">
<h1><strong>ღ¸.🌸´`🌸.¸¸ღ - A3 - ღ¸.🌸´`🌸.¸¸ღ</strong></h1>

<h2><strong>ʚ🌹ɞ Ahumada Vizcarra Eudaldo Alejandro ʚ🌹ɞ</strong></h2>
</div>

●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●
<div align="center">
<h2><strong> ⭐Descripción del juego y sus caracteristicas⭐</strong></h2>
</div>

A3 es un juego de plataformas donde un personaje "Hero", tiene que ir consiguiendo monedas al rededor del juego para poder permitirle llegar a la meta, este juego consta de 2 niveles y 1 meta, el primer nivel donde se tiene que subir hasta llegar a la puerta para cruzar al siguiente nivel, y el segundo nivel donde es lo contrario, se tiene que bajar hasta poder llegar a la meta del juego, pero ojo esto no sera fácil ya que tendras que tener un puntuaje mínimo si quieres llegar a tu destino.

🔹 Este juego tiene 2 niveles y una meta 

🔹 Existe la presencia de 5 deiferentes tipos de plataformas 

🔹 Consta de un sistema de puntuaje en base a la recolección de monedas al rededor del juego 

🔹 Puedes guardar tu progreso y conseguir llegar a la meta de una forma mas facil, que su version beta.

●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●
<div align="center">
<h2><strong> ⭐Assest⭐</strong></h2>
</div>

🔹Door.png 

<img width="263" height="261" alt="image" src="https://github.com/user-attachments/assets/6168627e-3733-41f8-8f5b-52e1e9ddd95d" /> 

■━■━■━■■━■━■━■■━■━■━■ 

🔹Hero_006_Idle.png 

<img width="262" height="258" alt="image" src="https://github.com/user-attachments/assets/faa053cc-e1e2-44d6-a97d-e9d5230c3477" /> 

■━■━■━■■━■━■━■■━■━■━■

🔹Moneda.png 

<img width="261" height="260" alt="image" src="https://github.com/user-attachments/assets/39658390-2785-4b89-9d35-7c41235a9d68" /> 

■━■━■━■■━■━■━■■━■━■━■

🔹Platform.png 

<img width="265" height="250" alt="image" src="https://github.com/user-attachments/assets/f1f8c3d2-b70b-4f40-bf84-3debbf50283b" /> 

●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●
<div align="center">
<h2><strong> ⭐Descripcción de Scripts⭐</strong></h2>
</div>

🔹Door.gd 

➽ Qué es: Un Area2D que controla el paso al siguiente nivel.

  🦋 Exporta: 
  
    ☛ puntaje_necesario (por defecto 1000). 
    
    ☛ siguiente_nivel (ruta .tscn del próximo nivel). 
    
    ☛ path_mensaje (un Label para mostrar avisos).

  🦋 Al entrar el jugador: 
  
    ☛ Verifica que el cuerpo pertenezca al grupo "jugador". 
    
    ☛ Lee su puntaje. 
    
    ☛ Si no alcanza el mínimo, muestra durante 2s el mensaje “Necesitas %d puntos para avanzar”. 
    
    ☛ Si lo alcanza y siguiente_nivel no está vacío, hace change_scene_to_file(siguiente_nivel).

■━■━■━■■━■━■━■■━■━■━■ 

🔹moneda.gd  

➽ Qué es: Un Area2D que representa una moneda recolectable.

  🦋 Variables y configuración: 
  
    ☛ valor_puntos (por defecto 200) determina cuántos puntos da la moneda. 
    
    ☛ Se agrega al grupo "moneda" para facilitar su búsqueda en el juego.

  🦋 Al iniciar (_ready()): 
  
    ☛ Conecta la señal body_entered a _on_body_entered.

  🦋 Al detectar colisión (_on_body_entered): 
  
    ☛ Verifica si el cuerpo pertenece al grupo "jugador". 
    
    ☛ Llama a sumar_puntos(valor_puntos) en el jugador. 
    
    ☛ Se destruye a sí misma con queue_free().


■━■━■━■■━■━■━■■━■━■━■

🔹nivel_0.gd y nivel_1.gd 

➽ Qué es: Script de Node2D que gestiona el puntaje en la escena usando señales de monedas.

  🦋 Variables y configuración: 
  
    ☛ puntos (contador total de la escena). 
    
    ☛ puntos_label (referencia a la etiqueta PuntosLabel dentro de UI).

  🦋 Al iniciar (_ready()): 
  
    ☛ Conecta a todas las monedas del grupo "moneda" para recibir la señal moneda_recolectada.

  🦋 Al recolectar una moneda (_on_moneda_recolectada): 
  
    ☛ Incrementa puntos en 200. 
    
    ☛ Actualiza el texto de puntos_label.

  🦋 Métodos adicionales: 
  
    ☛ obtener_puntos() devuelve el puntaje actual.


■━■━■━■■━■━■━■■━■━■━■

🔹personaje.gd  

➽ Qué es: Un CharacterBody2D que controla el jugador, su movimiento, puntaje y sistema de guardado/carga.

  🦋 Variables y configuración:  
  
    ☛ vida, puntaje, velocidad, gravedad, fuerza_salto. 
    
    ☛ label_puntaje_path (ruta exportada para mostrar el puntaje en pantalla). 
    
    ☛ Pertenece al grupo "jugador".

  🦋 Movimiento y control (_physics_process): 
  
    ☛ Aplica gravedad si no está en el suelo. 
    
    ☛ Mueve al jugador horizontalmente con las teclas configuradas. 
    
    ☛ Permite saltar si está en el suelo.

  🦋 Guardar y cargar: 
  
    ☛ Acción "guardar": guarda en JSON el nivel actual, puntaje y posición. 
    
    ☛ Acción "cargar": lee el JSON y restaura datos si coinciden con el nivel.

  🦋 Puntaje: 
  
    ☛ sumar_puntos(cantidad) aumenta el puntaje y actualiza el Label.


■━■━■━■■━■━■━■■━■━■━■

🔹plataforma.gd

➽ Qué es: Un Area2D que representa diferentes tipos de plataformas con comportamiento propio.

  🦋 Tipos de plataforma (enum TipoPlataforma): 
  
    ☛ FIJA: permanece estática (color verde). 
    
    ☛ OSCILATORIA: se mueve horizontalmente de un lado a otro (color azul). 
    
    ☛ FRÁGIL: desaparece medio segundo después de ser tocada (color rojo). 
    
    ☛ REBOTE: impulsa al jugador hacia arriba (color amarillo). 
    
    ☛ MUERTE: reinicia la escena al ser tocada (color blanco).

  🦋 Lógica principal (_on_body_entered): 
  
    ☛ Detecta si el jugador entra en contacto. 
    
    ☛ Ejecuta la acción correspondiente según el tipo de plataforma.

  🦋 Movimiento especial: 
  
    ☛ oscilar() usa un Tween para mover la plataforma de un lado a otro en bucle.


●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●
<div align="center">
<h2><strong> ⭐Videos⭐</strong></h2>
</div>

■━■━■━■■━■━■━■■━■━■━■

https://github.com/user-attachments/assets/b22755a9-cba6-4e47-8ab0-5ff818cc5a60

■━■━■━■■━■━■━■■━■━■━■

https://github.com/user-attachments/assets/e22a6a64-1bfe-447c-955a-64e9eed86c7a

■━■━■━■■━■━■━■■━■━■━■

https://github.com/user-attachments/assets/8b644b5a-c0b7-449a-8035-0c97fb1bdc97



●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●～●
<div align="center">
<h2><strong> ⭐Comentarios finales⭐</strong></h2>
</div>

El haber logrado desarrollar una version un poco mas completa del juego beta "A3", fue algo enriquecedor para poder obetner mas conocimiento dentro del mismo godot, fue un poco dificil ya que el agregar el nuevo sistema de guardado y cargado entro en conflicto con otros scripts que tambien tuvieron que ser modificados para acoplarse al nuevo juego, pero al final se obtuvo el resultado esperado totalmente.
