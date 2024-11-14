import turtle

# Configuración inicial de la ventana
screen = turtle.Screen()
screen.setup(width=800, height=600)
screen.title("Aventura RPG")
screen.bgcolor("black")

# Crear canvas para dibujar el recuadro de diálogo
canvas = screen.getcanvas()

# Función para dibujar el fondo del recuadro de diálogo en el canvas
def draw_dialogue_box():
    canvas.create_rectangle(50, 450, 750, 550, fill="blue", outline="blue")  # Borde del cuadro
    canvas.create_rectangle(60, 460, 740, 540, fill="black", outline="black")  # Fondo del cuadro

# Llamar a la función para que se dibuje el recuadro de diálogo
draw_dialogue_box()

# Protagonista
cecil = turtle.Turtle()
cecil.shape("triangle")
cecil.color("green")
cecil.penup()
cecil.speed(0)

# Movimiento del protagonista
move_speed = 15

def move_up():
    y = cecil.ycor()
    cecil.sety(y + move_speed)

def move_down():
    y = cecil.ycor()
    cecil.sety(y - move_speed)

def move_left():
    x = cecil.xcor()
    cecil.setx(x - move_speed)

def move_right():
    x = cecil.xcor()
    cecil.setx(x + move_speed)

# Controles de movimiento
screen.listen()
screen.onkey(move_up, "w")
screen.onkey(move_down, "s")
screen.onkey(move_left, "a")
screen.onkey(move_right, "d")

# Variable para el diálogo en pantalla
dialogue_turtle = turtle.Turtle()
dialogue_turtle.hideturtle()
dialogue_turtle.penup()
dialogue_turtle.color("black")

# Función para mostrar el diálogo en el recuadro
def display_dialogue(text):
    dialogue_turtle.clear()
    dialogue_turtle.goto(-330, -220)  # Posición dentro del recuadro
    dialogue_turtle.write(text, align="left", font=("Britannic Bold", 18, "normal"))

#dialogo 2
def display_dialogue2(text):
    dialogue_turtle.clear()
    dialogue_turtle.goto(-330, -220)  # Posición dentro del recuadro
    dialogue_turtle.write(text, align="left", font=("Britannic Bold", 18, "normal"))

# Diálogos y respuestas con estructura de árbol
def initial_dialogue():
    display_dialogue("Cecil: 'Me siento...raro...liviano, me siento perdido...¿Donde estoy?'")
    screen.ontimer(lambda: display_dialogue("Voz misteriosa: 'Cecil, debes salvar este y otros mundos del mal.'"), 2000)
    screen.ontimer(lambda: display_dialogue("Cecil: ¿de quien es esa voz?,todo está oscuro..."), 4000)
    screen.ontimer(lambda: display_dialogue("Cecil: pero no tengo los ojos cerrados,mire a mi alrededor y lo unico que vi fue...oscuridad.'"), 6000)
    screen.ontimer(lambda: display_dialogue("Cecil: mire a mi alrededor y lo unico que vi fue...oscuridad.'"), 8000)
    screen.ontimer(option_1, 10000)

# Opciones de respuesta
def option_1():
    display_dialogue("Presiona '1' para preguntar: '¿Quién eres?'\nPresiona '2' para preguntar: '¿Donde estoy?'")
    screen.onkey(response_1, "1")
    screen.onkey(response_2, "2")

# Respuestas
def response_1():
    display_dialogue("Voz misteriosa: 'yo soy lo que ustedes humanos llamarían una diosa, lamento informarte que has muerto.'")
    screen.ontimer(option_2, 2000)

def response_2():
    display_dialogue("Voz misteriosa: 'estas en el limbo, sufriste un accidente y terminaste en este lugar '")
    screen.ontimer(option_3, 2000)

# Ramificaciones de respuesta
def option_2():
    display_dialogue("Presiona '1' para preguntar: '¿Que me va a pasar ahora?'\nPresiona '2' para preguntar: '¿y ahora que puedo hacer?'")
    screen.onkey(response_3, "1")
    screen.onkey(response_4, "2")

def option_3():
    display_dialogue("Presiona '1' para decir: 'entiendo¿que necesitas que haga?'\nPresiona '2' para preguntar: '¿Como puedo ayudarte?'")
    screen.onkey(response_5, "1")
    screen.onkey(response_6, "2")

# Respuestas adicionales
def response_3():
    display_dialogue("Voz misteriosa: 'Este viaje será difícil, pero en tu interior reside la fuerza que puede cambiar destinos. Busca aliados, pues necesitarás de su ayuda.'")
    screen.ontimer(change_to_pueblo_scene, 2000)  # Cambia a la escena del pueblo

def response_4():
    display_dialogue("Voz misteriosa: 'Todo comienza aquí, en este pueblo desconocido. Explora y descubre tu propósito.'")
    screen.ontimer(change_to_pueblo_scene, 2000)  # Cambia a la escena del pueblo

def response_5():
    display_dialogue("Voz misteriosa: 'En un bosque cercano, yace una espada olvidada, bendecida por antiguas fuerzas. Será esencial para tu misión.'")
    screen.ontimer(change_to_pueblo_scene, 2000)  # Cambia a la escena del pueblo

def response_6():
    display_dialogue("Voz misteriosa: 'El equilibrio de muchos mundos está en tus manos. Tu misión es crucial para la paz.'")
    screen.ontimer(change_to_pueblo_scene, 2000)  # Cambia a la escena del pueblo

# Cambiar a la escena del gremio
def change_to_pueblo_scene():
    screen.bgpic("C:\\Users\\HP\\OneDrive\\Escritorio\\aventura rpg\\puebloinicial.gif")
    dialogue_turtle.clear()
    draw_dialogue_box()
    display_dialogue("Cecil: debo buscar un gremio en este pueblo")
    screen.ontimer(change_to_guild_scene, 3000)

# Cambiar a la escena del gremio
def change_to_guild_scene():
    screen.bgpic("C:\\Users\\HP\\OneDrive\\Escritorio\\aventura rpg\\gremio-de-aventurero.gif")
    dialogue_turtle.clear()
    draw_dialogue_box()
    display_dialogue2("Recepcionista: 'Bienvenido al gremio, ¿eres un nuevo aventurero?'")
    screen.ontimer(elysia_intro, 3000)

# Introducción de Elysia
def elysia_intro():
    draw_dialogue_box()
    display_dialogue("Elysia: '¡Hola! No te había visto antes. ¿Eres nuevo aquí?'")
    screen.ontimer(option_elysia, 3000)

# Opciones de respuesta con Elysia
def option_elysia():
    draw_dialogue_box()
    display_dialogue("Presiona '1' para decir: 'Sí, acabo de llegar al pueblo.'\nPresiona '2' para decir: '¿Y tú quién eres?'")
    screen.onkey(elysia_response_1, "1")
    screen.onkey(elysia_response_2, "2")

def elysia_response_1():
    draw_dialogue_box()
    display_dialogue("Elysia: '¡Genial! Espero que podamos hacer misiones juntos pronto.'")
    screen.ontimer(option_elysia_2, 3000)

def elysia_response_2():
    draw_dialogue_box()
    display_dialogue("Elysia: 'Oh, soy Elysia. Soy una aventurera también. ¡Encantada de conocerte!'")
    screen.ontimer(option_elysia_2, 3000)

# Opciones adicionales de diálogo con Elysia después de la presentación inicial
def option_elysia_2():
    draw_dialogue_box()
    display_dialogue("Presiona '1' para preguntar: '¿Qué puedes decirme sobre este gremio?'\nPresiona '2' para preguntar: '¿Cómo es ser aventurera aquí?'")
    screen.onkey(elysia_response_3, "1")
    screen.onkey(elysia_response_4, "2")

def elysia_response_3():
    draw_dialogue_box()
    display_dialogue("Elysia: 'El gremio es donde los aventureros tomamos misiones para ayudar al pueblo. Puedes encontrar trabajos interesantes y otros aventureros con los que hacer equipo.'")
    screen.ontimer(elysia_followup, 3000)

def elysia_response_4():
    draw_dialogue_box()
    display_dialogue("Elysia: 'Ser aventurera aquí es increíble. Siempre hay algo emocionante, pero también hay peligros. ¿Tienes experiencia combatiendo?'")
    screen.ontimer(elysia_followup, 3000)

# Diálogo de seguimiento tras las respuestas adicionales
def elysia_followup():
    draw_dialogue_box()
    display_dialogue("Elysia: 'Si necesitas ayuda o tienes preguntas, solo búscame en el gremio. ¡Me encantaría ayudarte!'")
    screen.ontimer(next_act, 3000)  # Procede al siguiente acto

# Función para avanzar al siguiente acto
def next_act():
    # Aquí podríamos cambiar a un nuevo escenario o iniciar un nuevo evento
    display_dialogue("Cecil: 'Es hora de prepararme y aceptar mi primera misión.'")
    screen.ontimer(elf_mission_intro, 3000)

# Diálogo de introducción de la misión
def elf_mission_intro():
    draw_dialogue_box()
    display_dialogue("Niña Elfa: '¡Ayuda! ¡Mi pueblo está siendo atacado por una horda de duendes!'")
    screen.ontimer(decision_to_help, 3000)

# Decisión para aceptar la misión
def decision_to_help():
    draw_dialogue_box()
    display_dialogue("Cecil: '¿Debemos ayudarla, Elysia?'")
    screen.onkey(accept_mission, "y")  # Presiona 'y' para aceptar
    screen.onkey(ask_for_more_info, "n")  # Presiona 'n' para pedir más información
    screen.listen()

def accept_mission():
    draw_dialogue_box()
    display_dialogue("Elysia: 'Claro, debemos ayudar. No podemos dejar que su pueblo caiga.'")
    screen.ontimer(go_to_elf_village, 3000)

def ask_for_more_info():
    draw_dialogue_box()
    display_dialogue("Cecil: 'Antes de ir, ¿qué puedes decirnos sobre estos duendes?'")
    screen.ontimer(elf_explanation, 3000)

# La niña elfa explica el ataque de los duendes
def elf_explanation():
    draw_dialogue_box()
    display_dialogue("Niña Elfa: 'Son duendes feroces, liderados por uno muy fuerte. Han destruido nuestras defensas.'")
    screen.ontimer(decision_to_help, 3000)

# Camino al pueblo elfo
def go_to_elf_village():
    screen.bgpic("C:\\Users\\HP\\OneDrive\\Escritorio\\aventura rpg\\bosque-elfico.gif")  # Imagen de camino
    dialogue_turtle.clear()
    draw_dialogue_box()
    display_dialogue("Cecil y Elysia: 'Estamos en camino al pueblo elfo...'")
    screen.ontimer(arrive_at_elf_village, 3000)

# Llegada al pueblo elfo en peligro
def arrive_at_elf_village():
    screen.bgpic("C:\\Users\\HP\\OneDrive\\Escritorio\\aventura rpg\\aldea-elfica.gif")  # Imagen del pueblo destruido
    dialogue_turtle.clear()
    draw_dialogue_box()
    display_dialogue("Cecil: '¡El pueblo está en ruinas! Los duendes han causado estragos.'")
    screen.ontimer(decision_before_battle, 3000)

# Decisión antes de entrar en batalla
def decision_before_battle():
    draw_dialogue_box()
    display_dialogue("Elysia: '¿Deberíamos buscar sobrevivientes primero o enfrentarlos de inmediato?'")
    screen.onkey(search_survivors, "s")  # Presiona 's' para buscar sobrevivientes
    screen.onkey(attack_immediately, "a")  # Presiona 'a' para atacar de inmediato
    screen.listen()

def search_survivors():
    draw_dialogue_box()
    display_dialogue("Cecil: 'Primero, vamos a buscar si alguien necesita ayuda.'")
    screen.ontimer(find_elf, 3000)

def attack_immediately():
    draw_dialogue_box()
    display_dialogue("Cecil: '¡Vamos directo al ataque! No hay tiempo que perder.'")
    screen.ontimer(start_battle_dialogue, 3000)

# Encuentran a una elfa en los restos del pueblo
def find_elf():
    draw_dialogue_box()
    display_dialogue("Elfa misteriosa: '¡Gracias por venir! Estoy aquí para luchar a su lado.'")
    screen.ontimer(start_battle_dialogue, 3000)

# Diálogo de inicio de batalla
def start_battle_dialogue():
    draw_dialogue_box()
    display_dialogue("Elysia: '¡Prepárate, vienen más duendes!'")
    screen.ontimer(after_battle, 3000)

# Diálogo después de la batalla
def after_battle():
    draw_dialogue_box()
    display_dialogue("Cecil: 'Gracias por tu ayuda. ¿Cómo te llamas?'")
    screen.ontimer(next_steps, 3000)

# Opciones de próxima decisión
def next_steps():
    draw_dialogue_box()
    display_dialogue("Elfa misteriosa: 'Soy Sylvina. ¿Planean quedarse en el pueblo o seguir adelante?'")
    screen.onkey(stay_and_help, "h")  # Presiona 'h' para quedarse y ayudar a reconstruir
    screen.onkey(move_forward, "m")   # Presiona 'm' para continuar su misión
    screen.listen()

def stay_and_help():
    draw_dialogue_box()
    display_dialogue("Cecil: 'Nos quedaremos y ayudaremos a reconstruir el pueblo.'")
    # Continúa la narrativa o añade más diálogos para la decisión de quedarse

def move_forward():
    draw_dialogue_box()
    display_dialogue("Cecil: 'Vamos a seguir adelante. Nuestra misión aún no ha terminado.'")
    # Continúa la narrativa con el siguiente escenario

# Menú de inicio
def show_intro():
    dialogue_turtle.goto(0, 200)
    dialogue_turtle.write("¡Bienvenido a la Aventura RPG!", align="center", font=("Arial", 24, "bold"))
    dialogue_turtle.goto(0, 150)
    dialogue_turtle.write("Presiona ESPACIO para comenzar", align="center", font=("Arial", 18, "normal"))
    screen.onkey(start_game, "space")

# Iniciar el juego
def start_game():
    screen.clear()
    draw_dialogue_box()  # Dibuja el recuadro al inicio del juego
    screen.bgpic("")
    initial_dialogue()

show_intro()
screen.mainloop()

<!---
Erick404821/Erick404821 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
