# POO-R2
UML de algo real
### Code
https://es.slideshare.net/slideshow/por-qu-no-funciona-transmilenio-nueva-propuesta/11961002
```mermaid
classDiagram
    class Parada {
        +String id_parada
        +String nombre
        +Coordinates ubicacion        // latitud, longitud
        +String direccion
        +String zona
        +List~Ruta~ rutas
        +String tipo_parada           // Regular, Troncal, Estacion, Alimentadora, A solicitud
        +String tipo_anden            // Simple, central, isla
        +int capacidad_espera
        +int asientos
        +int Puntos_de_Recarga 
        +int Empleados 
        +Boolean marquesina
        +Boolean cubierta
        +Boolean iluminacion
        +Boolean senalizacion          // señal estática o dinámica
        +Boolean accesible_discapacidad
        +Float tiempo_estimado_espera
        +int demanda_promedio
        +Date ultima_mantenimiento
        +String estado                // Ej: Operativa, Necesita Reparación, Inactiva

        +void mostrar_informacion()
        +void agregar_ruta(Ruta ruta)
        +void remover_ruta(Ruta ruta)
        +void actualizar_estado(String nuevo_estado)
        +Float calcular_tiempo_de_espera()
        +Boolean es_accesible()
        +void programar_mantenimiento(Date fecha)
    }

    class ParadaPortalNorte {
        +String id_parada = "PN-001"
        +String nombre = "Portal Norte"
        +String direccion = "Autopista Norte con Calle 175‑176, Bogotá"
        +String zona = "Norte"
        +List~Ruta~ rutas = ["B924", "B75", "B27", "Alimentador Mirandela", "Alimentador Verbenal"]
        +String tipo_parada = "Estacion Troncal"
        +String tipo_anden = "Central"
        +int capacidad_espera = 1000
        +int asientos = 40
        +int Puntos_de_Recarga = 0
        +int Empleados = 8
        +Boolean marquesina = true
        +Boolean cubierta = true
        +Boolean iluminacion = true
        +Boolean senalizacion = true
        +Boolean accesible_discapacidad = true
        +Float tiempo_estimado_espera = 5.0
        +int demanda_promedio = 5000
        +Date ultima_mantenimiento = 2025‑08‑01
        +String estado = "Operativa"

        +void mostrar_informacion()
        +void agregar_ruta(Ruta ruta)
        +void remover_ruta(Ruta ruta)
        +void actualizar_estado(String nuevo_estado)
        +Float calcular_tiempo_de_espera()
        +Boolean es_accesible()
        +void programar_mantenimiento(Date fecha)
    }

    class ParadaSITP_IPN {
        +String id_parada = "SITP‑132"
        +String nombre = "Av. 9 con 127A - Instituto Pedagógico Nacional"
        +Coordinates ubicacion = (4.707, -74.054)   // valor aproximado
        +String direccion = "Avenida 9 con Calle 127A, Bogotá"
        +String zona = "Norte"
        +List~Ruta~ rutas = ["18‑2 Barrancas", "736 Calle 222 ‑ Paraíso", "T11 Calle 222 ‑ Alpes"]
        +String tipo_parada = "Paradero Zonal"
        +String tipo_anden = "Simple"
        +int capacidad_espera = 200
        +int asientos = 10
        +int Puntos_de_Recarga = 0
        +int Empleados = 2
        +Boolean marquesina = false
        +Boolean cubierta = true
        +Boolean iluminacion = true
        +Boolean senalizacion = true
        +Boolean accesible_discapacidad = false
        +Float tiempo_estimado_espera = 7.5
        +int demanda_promedio = 800
        +Date ultima_mantenimiento = 2025‑08‑15
        +String estado = "Operativa"

        +void mostrar_informacion()
        +void agregar_ruta(Ruta ruta)
        +void remover_ruta(Ruta ruta)
        +void actualizar_estado(String nuevo_estado)
        +Float calcular_tiempo_de_espera()
        +Boolean es_accesible()
        +void programar_mantenimiento(Date fecha)
    }

    Parada <|-- ParadaPortalNorte
    Parada <|-- ParadaSITP_IPN


    class Ruta {
        +String id_ruta
        +String nombre
        +String Indice ruta
        +String tipo_servicio              // ej: Urbana, Alimentadora, Especial, Troncal
        +List~Parada~ paradas
        +Time horario_inicio
        +Time horario_fin
        +String origen
        +String destino
        +List~String~ dias_operacion       // Ej: ["Lunes","Martes",...]
        +Float duracion_promedio           // minutos para recorrer toda la ruta
        +Float longitud_ruta               // kilómetros
        +String zona                       // barrios o sector por donde pasa
        +Int numero_pasajeros_promedio     // demanda estimada
        +List~String~ sentidos             // ej: ["A->B", "B->A"]
        +String operador
        +String estado_operativo           // Activa, Suspendida, etc.
        +Decimal costo_base
        +

        +List~Parada~ obtener_paradas()
        +void agregar_parada(Parada parada, int posicion)
        +void remover_parada(Parada parada)
        +Float calcular_tiempo_total()
        +Float calcular_distancia_total()
        +Boolean es_activa(Date fecha, String dia, Time hora)
        +Float get_frecuencia_en_horario(Time hora)
        +String obtener_sentido(String origen, String destino)
        +List~Parada~ obtener_paradas_cercanas(Coordenada ubicacion, Float distancia_max)
        +String toString()
    }


    %% Instancia de la Ruta B27 (TransMilenio)
    class RutaB27 {
        +String nombre = "B27"
        +String tipo = "Troncal"
        +List~String~ paradas = ["Portal Tunal", "Calle 40 Sur", "AV. Jiménez", "Marly", "Calle 72", "Calle 76", "Calle 85"]
        +String recorrido = "Desde Portal Tunal hasta Portal Norte"
        +List~String~ horarios = ["Lunes a Viernes: 04:00-23:00", "Sábados: 05:00-23:00", "Domingos y Festivos: 05:00-22:00"]
        +String operador = "TransMilenio S.A."
        +String zona = "Avenida Caracas"
        +int flota = 10559
        +int flota_electrica = 1485
        +String toString()
    }

    %% Instancia de la Ruta 639 (SITP)
    class Ruta639 {
        +String nombre = "639"
        +String tipo = "Zonal"
        +List~String~ paradas = ["Calle 182", "Horizontes Norte", "San Antonio Norte", "La Granja Norte", "San Cristóbal Norte", "Cedritos", "Santa Bárbara Oriental", "Usaquén", "Santa Bárbara Occidental", "Pasadena", "La Castellana", "Las Ferias", "Metrópolis", "Bella Vista Occ.", "Bosque Popular", "El Salitre", "Ciudad Salitre Nor-Oriental", "Salazar Gómez", "Pradera", "Provivienda Oriental", "Alquería", "Venecia", "Muzú", "El Carmen", "Sierra Morena", "Santo Domingo"]
        +String recorrido = "Desde Calle 182 hasta Santo Domingo"
        +List~String~ horarios = ["Lunes a Viernes: 04:30-22:00", "Sábados: 05:00-22:00", "Domingos y Festivos: 05:00-21:00"]
        +String operador = "EGOBUS y CONSORCIO EXPRESS S.A.S"
        +String zona = "Usaquén - Perdomo"
        +int flota = 9299
        +int flota_electrica = 1485
        +String toString()
    }

    %% Relaciones
    Ruta <|-- RutaB27
    Ruta <|-- Ruta639

    class Bus {
        +String id_bus
        +String placa
        +String tipo                // Articulado, Biarticulado, Normal, Alimentador, etc.
        +int capacidad_maxima
        +String empresa_operadora
        +int numero_puertas
        +Float longitud
        +Float ancho
        +String tipo_combustible    // Diesel, electrico, híbrido
        +String estado_operativo     // Operativo, mantenimiento, fuera de servicio
        +Ruta ruta_actual
        +Conductor conductor
        +Date fecha_ultima_revision
        +Float kilometros_recorridos
        +int ocupacion_actual
        +Boolean accesible_discapacidad
        +string ubicacion

        +void asignar_conductor(Conductor c)
        +void asignar_ruta(Ruta r)
        +void iniciar_servicio()
        +void terminar_servicio()
        +void registrar_pasajeros(int numero)
        +void descargar_pasajeros(int numero)
        +boolean verificar_capacidad()
        +void realizar_mantenimiento(Date fecha)
        +Float calcular_tiempo_estimado_parada(Parada parada)
        +String toString()
    }


    %% Instancia de Bus Alimentador B924
    class BusB924 {
        +String id = "B924"
        +String tipo = "Alimentador"
        +String ruta = "Portal Norte - Club Campestre Cafam"
        +String operador = "TransMilenio S.A."
        +String zona = "Autopista Norte"
        +String color = "Verde"
        +int capacidad = 90
        +List~String~ paradas = ["Portal Norte", "Vereda Torca", "El Corozo", "La Floresta", "Parque Comercial Bima", "Calle 224", "La Santamaría", "Club Campestre Cafam"]
        +List~String~ horarios = ["Lunes a Viernes: 04:30-09:00", "Lunes a Viernes: 16:00-20:30"]
        +String toString()
    }

    %% Instancia de Bus Complementario L819
    class BusL819 {
        +String id = "L819"
        +String tipo = "Complementario"
        +String ruta = "Santa Inés - Portal 20 de Julio"
        +String operador = "SITP"
        +String zona = "Sur"
        +String color = "Naranja"
        +int capacidad = 50
        +List~String~ paradas = ["Santa Inés", "Portal 20 de Julio"]
        +List~String~ horarios = ["Lunes a Viernes: 04:00-21:00", "Sábados: 05:00-20:00"]
        +String toString()
    }

    %% Relaciones
    Bus <|-- BusB924
    Bus <|-- BusL819
    class Viaje {
        +String id_viaje
        +Usuario usuario
        +Tarjeta tarjeta_usada
        +Bus bus
        +Ruta ruta
        +Parada parada_origen
        +Parada parada_destino
        +DateTime hora_inicio
        +DateTime hora_fin
        +Float duracion
        +Float distancia
        +int numero_transbordos
        +String estado              // Planificado, EnCurso, Completado, Cancelado

        +void iniciar_viaje(Parada origen, DateTime hora)
        +void finalizar_viaje(Parada destino, DateTime hora)
        +Decimal calcular_costo()
        +void realizar_transbordo(Parada punto_transbordo)
        +Float get_tiempo_espera()
        +void cancelar()
        +String toString()
    }
    

    %% Subclase ViajeAlimentador
    class ViajeAlimentador {
        +String id = "A001"
        +String origen = "Portal Norte"
        +String destino = "Club Campestre Cafam"
        +String fecha = "2025-09-17"
        +String hora_salida = "04:30"
        +String hora_llegada = "05:15"
        +String tipo = "Alimentador"
        +String operador = "TransMilenio S.A."
        +String zona = "Norte"
        +int pasajeros = 85
        +String toString()
    }

    %% Subclase ViajeComplementario
    class ViajeComplementario {
        +String id = "C001"
        +String origen = "Santa Inés"
        +String destino = "Portal 20 de Julio"
        +String fecha = "2025-09-17"
        +String hora_salida = "04:00"
        +String hora_llegada = "04:30"
        +String tipo = "Complementario"
        +String operador = "SITP"
        +String zona = "Sur"
        +int pasajeros = 45
        +String toString()
    }

    %% Relaciones de herencia
    Viaje <|-- ViajeAlimentador
    Viaje <|-- ViajeComplementario


     class Usuario {
        +String id_usuario
        +String nombre
        +String documento_identidad
        +Date fecha_nacimiento
        +String direccion
        +String tipo_usuario           // Normal, Estudiante, AdultoMayor, Discapacidad
        +Tarjeta tarjeta
        +String Viaje Previo
        +List~Viaje~ historial_pagos
        +Decimal saldo_promedio_mensual
        +Date fecha_registro
        +String estatus               // Activo, Bloqueado, etc.

        +void registrarse()
        +void actualizar_datos(String nombre, String correo, String telefono, String direccion)
        +void asignar_tarjeta(Tarjeta tarjeta)
        +void realizar_viaje(Ruta ruta)
        +List~Viaje~ consultar_historial(Date inicio, Date fin)
        +Decimal calcular_gasto_total(Date inicio, Date fin)
        +Decimal aplicar_descuento()
        +void cambiar_preferencias(List~String~ nuevasPreferencias)
        +String toString()
    }

    %% Clase Sistema
    class Sistema {
        +String nombre
        +String tipo
        +List~Ruta~ rutas
        +List~Parada~ paradas
        +List~Vehiculo~ vehiculos
        +int numero_de_viajeros
        +int tarifa
        +List~String~ horarios
        +String gestion
        +List~String~ zonas
        +void agregar_ruta(Ruta ruta)
        +void agregar_vehiculo(Vehiculo vehiculo)
        +void registrar_viajero()
        +String toString()
    }

    %% Instancia concreta TransMilenio
    class TransMilenio {
        +nombre = "TransMilenio"
        +tipo = "Troncal"
        +numero_de_viajeros = 4000000
        +tarifa = 3200
        +gestion = "TransMilenio S.A."
        +zonas = ["Avenida Caracas", "Autopista Norte", "Avenida Suba", "Avenida 68"]
        +flota_total = 10559
        +flota_electrica = 1485
        +horarios = ["Lunes a Viernes: 04:00-23:00", "Sábados: 05:00-23:00", "Domingos y Festivos: 05:00-22:00"]
        +rutas = ["B27", "F28", "H27", "J24", "K305", "M82"]
        +void agregar_ruta(Ruta ruta)
        +void agregar_vehiculo(Vehiculo vehiculo)
        +void registrar_viajero()
        +String toString()
    }

    %% Instancia concreta SITP
    class SITP {
        +nombre = "SITP"
        +tipo = "Zonal"
        +numero_de_viajeros = 3000000
        +tarifa = 3200
        +gestion = "TransMilenio S.A."
        +zonas = ["Fontibón", "Usme", "Perdomo", "Suba Centro"]
        +flota_total = 9299
        +flota_electrica = 1485
        +horarios = ["Lunes a Viernes: 04:30-22:00", "Sábados: 05:00-22:00", "Domingos y Festivos: 05:00-21:00"]
        +rutas = ["639", "921", "20-4", "22-3", "18-2", "L819"]
        +void agregar_ruta(Ruta ruta)
        +void agregar_vehiculo(Vehiculo vehiculo)
        +void registrar_viajero()
        +String toString()
    }

    %% Relaciones
    Sistema <|-- TransMilenio
    Sistema <|-- SITP


        class Tarjeta {
        +String id_tarjeta
        +String tipo                 --> «TipoTarjeta»: Básica / Personalizada / Abono
        +Decimal saldo
        +Boolean habilitada
        +Date fecha_emision
        +Date fecha_vencimiento_abono
        +Boolean personalizada
        +List~Beneficio~ beneficios
        +Decimal saldo_credito       --> cuánto “debe” si se permite viaje a crédito
        +void recargar(Decimal monto)
        +void usar_para_pasaje()
        +void hacer_credito()
        +void bloquear()
        +void personalizar(Usuario usuario, String nombre, String docId)
        +Boolean verificar_abono()
    }
     
    class Conductor {
        +String id_conductor
        +String nombre
        +String documento_identidad
        +int edad
        +String licencia_categoria      // "C2", "C3", etc.
        +boolean licencia_vigente
        +int años_experiencia          // años en conducción de vehículos pesados
        +boolean sin_comparendos       // true si no hay comparendos vigentes
        +String nivel_educativo        // ej: "Básica Primaria", "Bachiller", etc.
        +boolean disponibilidad        // si está disponible para asignar viajes / turnos
        +List~Ruta~ rutas_asignadas    // rutas que puede conducir
        +String turno_actual           // ej: "Mañana", "Tarde", "Noche"
        +String concesionario          // para cual empresa opera
        +Date fecha_contratacion       // fecha en la que fue contratado

        +boolean validar_licencia()
        +boolean verificar_comparendos()
        +boolean puede_conducir(Ruta ruta)
        +void asignar_ruta(Ruta ruta)
        +void iniciar_turno()
        +void terminar_turno()
        +String toString()

        
    }

    





    
```

