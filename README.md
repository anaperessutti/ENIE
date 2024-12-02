<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Precios de Tatuajes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label {
            margin-top: 10px;
            display: block;
        }
        select, button {
            margin-top: 5px;
            padding: 10px;
            width: 100%;
            max-width: 300px;
        }
        #precio {
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Calculadora de Precios de Tatuajes</h1>
    <label for="estilo">Selecciona el estilo:</label>
    <select id="estilo">
        <option value="lineales">Lineales</option>
        <option value="solidos">Sólidos</option>
        <option value="neo_tradi">Neo Tradi</option>
        <option value="realismo_black_gray">Realismo Black & Gray</option>
        <option value="color_lineal">Color Lineal</option>
        <option value="color_solido">Color Sólido</option>
        <option value="neo_tradi_color">Neo Tradi Color</option>
        <option value="realismo_color">Realismo Color</option>
    </select>

    <label for="tamano">Selecciona el tamaño:</label>
    <select id="tamano">
        <option value="parche_5x5">Parche (hasta 5x5)</option>
        <option value="parche_10x10">Parche (hasta 10x10)</option>
        <option value="parche_15x15">Parche (hasta 15x15)</option>
        <option value="media_manga">Media manga</option>
        <option value="manga_completa">Manga completa</option>
        <option value="zona_completa">Zona completa</option>
    </select>

    <label for="zona">Selecciona la zona:</label>
    <select id="zona">
        <option value="brazo">Brazo</option>
        <option value="antebrazo">Antebrazo</option>
        <option value="pierna_superior">Pierna Superior</option>
        <option value="pierna_inferior">Pierna Inferior</option>
        <option value="cuello">Cuello</option>
        <option value="hombro">Hombro</option>
        <option value="codo">Codo</option>
        <option value="espalda">Espalda</option>
        <option value="pecho">Pecho</option>
        <option value="panza">Panza</option>
        <option value="rodilla">Rodilla</option>
        <option value="empeine">Empeine</option>
        <option value="manos">Manos</option>
        <option value="cola">Cola</option>
        <option value="teta">Teta</option>
        <option value="axilas">Axilas</option>
        <option value="costillas">Costillas</option>
    </select>

    <label for="complejidad">Selecciona el nivel de complejidad:</label>
    <select id="complejidad">
        <option value="1">Nivel 1</option>
        <option value="2">Nivel 2</option>
        <option value="3">Nivel 3</option>
    </select>

    <button onclick="calcularPrecio()">Calcular Precio</button>

    <div id="precio"></div>

    <script>
        function calcularPrecio() {
            const estilo = document.getElementById("estilo").value;
            const tamano = document.getElementById("tamano").value;
            const zona = document.getElementById("zona").value;
            const complejidad = document.getElementById("complejidad").value;

            // Definir precios base según estilo
            let precioBase;
            switch (estilo) {
                case "lineales":
                    precioBase = 35000;
                    break;
                case "solidos":
                    precioBase = 40000;
                    break;
                case "neo_tradi":
                    precioBase = 50000;
                    break;
                case "realismo_black_gray":
                    precioBase = 70000;
                    break;
                case "color_lineal":
                    precioBase = 40000;
                    break;
                case "color_solido":
                    precioBase = 45000;
                    break;
                case "neo_tradi_color":
                    precioBase = 60000;
                    break;
                case "realismo_color":
                    precioBase = 80000;
                    break;
                default:
                    precioBase = 5000; // Precio base por defecto
            }

            // Multiplicadores de tamaño
            let multiplicadorTamano = 1;
            switch (tamano) {
                case "parche_10x10":
                    multiplicadorTamano = 2;
                    break;
                case "parche_15x15":
                    multiplicadorTamano = 3;
                    break;
                case "media_manga":
                    multiplicadorTamano = 5;
                    break;
                case "manga_completa":
                    multiplicadorTamano = 10;
                    break;
                default:
                    multiplicadorTamano = 1;
            }

            // Multiplicadores de zona
            let multiplicadorZona = 1;
            switch (zona) {
                case "brazo":
                    if (tamano === "media_manga" || tamano === "manga_completa" || tamano === "zona_completa") {
                        multiplicadorZona = 1.15;
                    }
                    break;
                case "antebrazo":
                    if (tamano === "media_manga" || tamano === "manga_completa" || tamano === "zona_completa") {
                        multiplicadorZona = 1;
                    }
                    break;
                case "pierna_superior":
                    if (tamano === "media_manga" || tamano === "manga_completa" || tamano === "zona_completa") {
                        multiplicadorZona = 1.5;
                    }
                    break;
                case "pierna_inferior":
                    if (tamano === "media_manga" || tamano === "manga_completa" || tamano === "zona_completa") {
                        multiplicadorZona = 1.3;
                    }
                    break;
                case "cuello":
                    multiplicadorZona = 1.3;
                    break;
                case "hombro":
                    if (tamano === "parche_10x10" || tamano === "parche_15x15" || tamano === "media_manga" || tamano === "manga_completa" || tamano === "zona_completa") {
                        multiplicadorZona = 1.15;
                    }
                    break;
                case "codo":
                    multiplicadorZona = 1.2;
                    break;
                case "espalda":
                    multiplicadorZona = 1.15;
                    break;
                case "pecho":
                    multiplicadorZona = 1.15;
                    break;
                case "panza":
                    multiplicadorZona = 1.2;
                    break;
                case "rodilla":
                    multiplicadorZona = 1.2;
                    break;
                case "empeine":
                    multiplicadorZona = 1.15;
                    break;
                case "manos":
                    multiplicadorZona = 1.15;
                    break;
                case "cola":
                case "teta":
                    multiplicadorZona = 1.2;
                    break;
                case "axilas":
                    multiplicadorZona = 1.3;
                    break;
                case "costillas":
                    multiplicadorZona = 1.15;
                    break;
                default:
                    multiplicadorZona = 1; // Multiplicador por defecto
            }

            // Multiplicadores de complejidad
            let multiplicadorComplejidad = 1;
            switch (complejidad) {
                case "2":
                    multiplicadorComplejidad = 1.4;
                    break;
                case "3":
                    multiplicadorComplejidad = 1.85;
                    break;
                default:
                    multiplicadorComplejidad = 1;
            }

            // Calcular precio final
            const precioFinal = precioBase * multiplicadorTamano * multiplicadorZona * multiplicadorComplejidad;
            document.getElementById("precio").textContent = `Precio estimado: $${precioFinal.toFixed(2)} ARS`;
        }
    </script>
</body>
</html>
