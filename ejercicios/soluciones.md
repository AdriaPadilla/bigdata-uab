# Ejercicios Básicos

```python3
# Se responden los Ejercicios por orden de ejecución

var_1 = "esto es un ejercicio"
print(var_1)
nota = 10
asignatura = "big data"
text_final = f"en la {asignatura} he obtenido un {nota}"
print(text_final)

nota_2 = 5
nou_text = text_final.replace(f"{nota}", f"{nota_2}")
print(nou_text)

notas = ["5","7","6","4","8","2"]
alumnos = ["jaume","carla","pere","adrià","rafael","agnès"]

for i,n in zip(notas, alumnos):
    nota = int(i)+1
    print(nota, n)
```

# Ejercicio Obtención de datos

## Ejercicio A
```python3
llista = [
    "david",
    "dani",
    "marta",
    "jaume",
    "adria",
    "carla",
    "joan",
    "pere",
    "carla",
    "pere",
    "adria",
    "quico",
    "pere",
    "joan",
    "agustí",
    "adria",
    "joan",
    "adria",
    "siscu",
    "carles",
    "dani",
    "carla"
    ]

# ¿Quanta gent ha assistit?
unics = set(llista)

# Quants han assistit a més de dues sessions?

contador = 0
for nom in unics:
    aparicions = llista.count(nom)
    if aparicions > 2:
        contador = contador + 1

# percentatge
percentatge = round(100*(contador/len(unics)), 2)

# Print resultats
print("Han assistit un total de:", len(unics))
print("Han assistit a mes de 2 sessions:", contador)
print(f"percentatge mes de 2 sessions: {percentatge}%")
```

## Ejercicio B
```python3
notes = ["5","3","7","8","9.5","4","6,2"]
alumnes = ["adria","agnès","josep","rafa","cristina","Gemma","Eduard"]

# Primer arreglem el tema de les notes

notes_arreglades = [] # Crearem una nova llista on guardar les notes notes_arreglades

### https://stackoverflow.com/questions/402504/how-to-determine-a-python-variables-type

for nota in notes:
    if "." in nota:
        nota_arreglada = float(nota)
        notes_arreglades.append(nota_arreglada)
    elif "," in nota:
        nota_arreglada = float(nota.replace(",", "."))
        notes_arreglades.append(nota_arreglada)
    else:
        nota_arreglada = int(nota)
        notes_arreglades.append(nota_arreglada)

print(notes_arreglades)

for n, a in zip(notes_arreglades, alumnes):
    print(f"L'alumne/a {a} ha obtingut un {n} de nota final")

# Calcular el promig
promig = sum(notes_arreglades)/len(notes_arreglades)

# Imprimir el promig fent el redondeig a 1 decimal
print(f"el promig de l'aula és de {round(promig,1)}")

# Obtenir la nota més alta
valor_alt = max(notes_arreglades)
valor_alt_posicio = notes_arreglades.index(max(notes_arreglades))
print(valor_alt)
print(alumnes[valor_alt_posicio])

# Obtenir la nota més baixa
valor_baix = min(notes_arreglades)
valor_baix_posicio = notes_arreglades.index(min(notes_arreglades))
print(valor_baix)
print(alumnes[valor_baix_posicio])
```
### Ejercicio "mi primer Dataframe"

```python
# Importamos Pandas
import pandas as pd

# Elementos básicos (datos disponibles)
notes = [1,6,8,9,10,6,5]
alumnes = ["Jaume", "Carles", "Cristina", "Josep", "Rafael", "Agnès", "Marta"]
cognoms = ["Tort","Soldevila","Luna","Muñoz","Fernandez","Hernandez", "Llopart"]

noms_complets = []

for n, c in zip(alumnes, cognoms):
    nom_complet = f"{n} {c}"
    noms_complets.append(nom_complet)

print(noms_complets)

tuplas = []

for nom, nota in zip(noms_complets, notes):
    tupla = (nom, nota)
    tuplas.append(tupla)

print(tuplas)

notes_arreglades = []
for t in tuplas:
    nota = t[1]
    if nota >= 9:
        nota_nova = 10
        qualificacio = "matricula de honor"
        tupla_nova = (t[0], nota_nova, qualificacio)
        notes_arreglades.append(tupla_nova)
    else:
        nota_nova = nota+1
        if nota_nova < 5 :
            qualificacio = "suspendido"
        elif nota_nova >=5 and nota_nova <=6:
           qualificacio = "aprobado"
        elif nota_nova >6 and nota_nova <7:
            qualificacio = "bien"
        elif nota_nova >= 7 and nota_nova <9:
            qualificacio = "notable"
        else:
            qualificacio = "Excelente"

        tupla_nova = (t[0], nota_nova, qualificacio)
        notes_arreglades.append(tupla_nova)

print(notes_arreglades)

df = pd.DataFrame(notes_arreglades, columns=["nom", "nota","qualificacio"])
mitjana = sum(df["nota"])/len(df)
df["desviació"] = round(df["nota"]-mitjana,2)
print(df)
