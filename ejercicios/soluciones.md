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
notes = [5,"3","7",8,"9.5",4,"6,2"]
alumnes = ["adria","agnès","josep","rafa","cristina","Gemma","Eduard"]

# Primer arreglem el tema de les notes

notes_arreglades = [] # Crearem una nova llista on guardar les notes notes_arreglades

### https://stackoverflow.com/questions/402504/how-to-determine-a-python-variables-type

for nota in notes:
    tipus = type(nota)
    if tipus.__name__ == 'int':
        notes_arreglades.append(nota)
    else:
        if tipus.__name__ == 'str':
            if "." in nota:
                nota_arreglada = float(nota)
                notes_arreglades.append(nota)
            elif "," in nota:
                nota_arreglada = nota.replace(",", ".")
                notes_arreglades.append(nota)
            else:
                nota_arreglada = int(nota)
                notes_arreglades.append(nota)

print(notes_arreglades)

for n, a in zip(notes_arreglades, alumnes):
    print(f"L'alumne/a {a} ha obtingut un {n} de nota final")
```
