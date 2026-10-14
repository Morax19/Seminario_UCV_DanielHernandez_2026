# CONTEXTO DE SESIÓN — Documento de continuidad

> **Propósito:** este archivo permite retomar la asistencia de OpenCode en otra máquina/OS
> sin perder el contexto de lo trabajado. Basta con abrir OpenCode en la carpeta del
> proyecto y pedir al agente que lea este archivo.
> **Sugerencia:** el agente debe leerlo al inicio de la nueva sesión con la instrucción:
> *"Lee `CONTEXTO_SESION.md` y continuamos donde quedamos."*

**Última actualización:** 14 de octubre de 2026

---

## 1. Proyecto

- **Tipo:** Seminario (propuesta de tesis) — Escuela de Computación, Facultad de Ciencias,
  Universidad Central de Venezuela (Centro ISYS).
- **Autor:** Br. Daniel A. Hernández F. · **Tutor:** Prof. Iván Flores V. · **Año:** 2026.
- **Idea general del sistema (4 agentes de IA):**
  1. **Agente 1 — Extracción:** lee datos no estructurados de un dominio y extrae entidades/clases.
  2. **Agente 2 — Estructuración:** procesa las clases, construye una base de datos siguiendo
     reglas de una ontología y genera el Knowledge Graph.
  3. **Agente 3 — Respuesta GraphRAG:** tiene acceso al grafo, responde peticiones del usuario
     con una arquitectura GraphRAG y genera además respuestas estructuradas en JSON para
     poblar bases de conocimiento.
  4. **Agente 4 — BI:** genera un data warehouse / modelo dimensional para responder
     preguntas de inteligencia de negocios.
- **Objetivo global:** automatizar todo el proceso de BI: de datos crudos → fuentes de
  conocimiento estructuradas → reportes de BI.
- El agente de modelos debe poder correr **local o vía API**, con parámetros ajustables por
  el usuario (ese detalle es del Capítulo 4, no del 2).

## 2. Archivos del repositorio

| Archivo | Estado / rol |
|---|---|
| `Seminario_DanielHernandez_2026.md` | **Fuente de verdad.** 627 líneas. Capítulos 1 y 2. |
| `Seminario_DanielHernandez_2026.docx` | Generado desde el `.md` (ver §6). **Ignorado por git.** |
| `Cap4_Borrador_Tecnologias.md` | Sección de tecnologías + refs [38]-[48], **trasladada fuera del Cap. 2**; se integrará en el Capítulo 4. |
| `.gitignore` | Ignora `*.docx`, `*.doc`, `*.docm`, `~$*` — el usuario **solo quiere `.md` en GitHub**. |

- Repo git en `main`, sincronizado con `origin/main` (todo committeado y subido al 14/10/2026).
- **Backup del `.docx` original (pre-regeneración):** `/tmp/opencode/Seminario_DanielHernandez_2026.backup.docx`
  — ⚠️ es temporal; si la migración de OS lo borra, el original también está en el historial
  de git **solo si** se designora el docx (actualmente nunca fue commiteado).

## 3. Estado de los capítulos

- **Capítulo 1 — Problema de la Investigación:** escrito por el usuario, **NO se debe tocar aún**.
  ⚠️ **Desfase pendiente:** el Cap. 1 plantea una *investigación comparativa AgenticRAG vs
  GraphRAG vs RL para extracción de conceptos con LLM local*, pero el proyecto real es el
  **pipeline de 4 agentes para automatizar BI**. Decisión tomada: el Cap. 2 se enmarcó para el
  pipeline de 4 agentes y **el Cap. 1 se reescribirá en un pase aparte**.
  Faltan: *Objetivos Específicos* (lista vacía) y el título real (dice `TÍTULO`).
- **Capítulo 2 — Marco Teórico (COMPLETADO, 14/10/2026):** solo **definiciones teóricas**.
  Secciones en orden: IA → Aprendizaje Automático → optimización/pérdida/Entropía Cruzada →
  Redes Neuronales → Activación/ReLU/Aproximación Universal/Softmax → Descenso del gradiente →
  Backpropagation → lotes/SGD/mini-lotes/Momentum/Adam → Aprendizaje profundo → Modelos
  Generativos → Auto-supervisado → Transformers → Autoatención → Multicabezal/Posicional →
  LLMs → Generación autorregresiva/Atención causal → Código abierto y ejecución local →
  Ventana de contexto e inferencia local → Bases relacionales y vectoriales → RAG → Agentes →
  RAG Agéntico → **Sistemas Multiagente y Orquestación** → **Salidas Estructuradas y
  Generación Restringida por Esquema (JSON)** → Representación del Conocimiento → Ontologías →
  **Lenguajes y Estándares: RDF, OWL y SPARQL** → Grafos de Conocimiento → **Bases de Datos de
  Grafos** → GraphRAG → **Inteligencia de Negocios** → **Data Warehousing** → **Modelado
  Dimensional** → **NL2SQL / Text-to-SQL** → Referencias.
  (Las secciones en negrita son las agregadas en este trabajo.)
- **Capítulo 3:** no existe aún (probablemente metodología/evaluación).
- **Capítulo 4 — Propuesta de Solución:** pendiente; ya tiene el borrador de tecnologías.
- **Resumen:** vacío. **Índice General:** vacío (ofrecer campo TOC de Word al pedirlo).

## 4. Convenciones CRÍTICAS del documento (no romper)

1. **Citas estilo IEEE numerado:** en el texto solo `[n]`; la lista `**Referencias**` va al final.
   - **NO reintroducir backslashes:** el usuario eliminó `\[n\]` → ahora es `[n]` a secas
     (se veían mal en el `.md`). Actualmente hay **0** `\[` en el archivo; mantenerlo así.
   - Numeración actual: **[1]-[18] = lista original** (orden alfabético, no renumerar);
     **[19]-[37] = añadidas, en orden de primera aparición en el texto.**
   - Regla de control: *toda referencia definida está citada y viceversa* (auditoría en §6).
   - Las refs [38]-[48] (herramientas) están **fuera**, en el borrador del Cap. 4.
2. **Formato del Markdown (heredado del export Word→md):**
   - Encabezados = línea independiente en negrita: `**Título de sección**` (sin `#`).
   - Párrafos de cuerpo **inician con un tabulador** (`\t`); las listas y encabezados, no.
   - Fórmulas en `$$...$$` o `$...$` (LaTeX) — Pandoc las convierte a ecuaciones nativas de Word.
   - Imágenes al inicio referenciadas por `[image1]…[image3]` con definiciones base64 al final
     del archivo (líneas larguísimas; **no tocar**).
3. **Estilo de redacción:** español académico, formal, voz pasiva/impersonal, 1 solo autor.
4. **Cap. 2 = solo teoría.** Cualquier "se usará X", "el agente N hará Y", "este proyecto adopta…"
   pertenece al **Capítulo 4**. Si aparece, generalizarlo ("en las arquitecturas de GraphRAG…",
   "un sistema NL2SQL típico…").

## 5. Pila tecnológica propuesta (para el Capítulo 4)

Ya escrita y justificada en `Cap4_Borrador_Tecnologias.md`:
Ollama + llama.cpp (local, GGUF/cuantización) · vLLM/PagedAttention (GPU) · API compatible con
OpenAI (remoto, mismo cliente) · Python + LangGraph (orquestación de grafos de estado) ·
Pydantic + JSON Schema + decodificación restringida (Outlines) · Chroma (vectorial embebible) ·
PostgreSQL + pgvector · DuckDB (analítico embebido sobre Parquet) · Neo4j + Cypher (grafo) ·
dbt (modelado dimensional como código) · Apache Superset / Metabase (tableros).
Estándares teóricos ya cubiertos en el Cap. 2: RDF/RDFS/OWL/SPARQL/SHACL, Kimball (dimensional).

## 6. Recetas técnicas reproducibles

### 6.1 Regenerar el `.docx` desde el `.md` (se hizo el 14/10/2026)

En el OS nuevo hace falta: `python3` (>=3.11) y red. Todo lo demás se instala en un venv:

```bash
python3 -m venv /tmp/opencode/pandocenv
/tmp/opencode/pandocenv/bin/pip install pypandoc_binary python-docx
```

Script de conversión + post-proceso (replica el formato del original: Times New Roman 12,
interlineado 1.5, justificado, sangría 0.5", portada centrada, Carta, márgenes 4/3 cm,
encabezado con PAGE alineado a la derecha, `titlePg`, numeración desde 0, logos tamaño original):

```python
# /tmp/opencode/pandocenv/bin/python regenerar_docx.py
import docx, zipfile, re, shutil, subprocess, os
from docx.shared import Pt, Cm, Inches, Emu
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

MD, ORIG = 'Seminario_DanielHernandez_2026.md', 'Seminario_DanielHernandez_2026.docx'
GEN = '/tmp/opencode/gen.docx'
PANDOC = '/tmp/opencode/pandocenv/lib/python3.12/site-packages/pypandoc/files/pandoc'

# 1) formato del original (hacerlo ANTES de sobreescribir)
o = docx.Document(ORIG)
centrados = {p.text.strip() for p in o.paragraphs
             if p.alignment == WD_ALIGN_PARAGRAPH.CENTER and p.text.strip()}
extents = [(int(a), int(b)) for a, b in re.findall(
    r'<wp:extent cx="(\d+)" cy="(\d+)"/>',
    zipfile.ZipFile(ORIG).read('word/document.xml').decode('utf8', 'ignore'))]

# 2) pandoc
subprocess.run([PANDOC, MD, '-f', 'markdown', '-t', 'docx', '-o', GEN], check=True)

# 3) post-proceso
d = docx.Document(GEN)
for st in d.styles:
    try:
        if st.font is not None: st.font.name = 'Times New Roman'
    except Exception: pass
n = d.styles['Normal']
n.font.name = 'Times New Roman'; n.font.size = Pt(12)
n.paragraph_format.space_after = Pt(8); n.paragraph_format.space_before = Pt(0)

centrados_en_doc = indentados = justificados = 0
for i, p in enumerate(d.paragraphs):
    txt = p.text.strip(); pf = p.paragraph_format; pf.line_spacing = 1.5
    tiene_imagen = bool(p._p.findall('.//' + qn('w:drawing')))
    if txt in centrados or (tiene_imagen and i < 5):
        p.alignment = WD_ALIGN_PARAGRAPH.CENTER; centrados_en_doc += 1; continue
    if not txt: continue
    p.alignment = WD_ALIGN_PARAGRAPH.JUSTIFY; justificados += 1
    es_lista = p._p.find('.//' + qn('w:numPr')) is not None
    es_titulo = all(r.bold for r in p.runs if r.text.strip())
    if (p.style.name in ('Body Text', 'First Paragraph') and not es_lista
            and not es_titulo and not txt.startswith('[')):
        pf.first_line_indent = Inches(0.5); indentados += 1
    for r in p.runs: r.font.name = 'Times New Roman'

sec = d.sections[0]
sec.header.is_linked_to_previous = False
hp = sec.header.paragraphs[0] if sec.header.paragraphs else sec.header.add_paragraph()
for r in list(hp.runs): r._r.getparent().remove(r._r)
hp.alignment = WD_ALIGN_PARAGRAPH.RIGHT
run = hp.add_run()
for tag, val in (('w:fldChar','begin'), None, ('w:fldChar','separate'), ('w:fldChar','end')):
    if tag is None:
        it = OxmlElement('w:instrText'); it.set(qn('xml:space'),'preserve'); it.text='PAGE'
        run._r.append(it)
    else:
        fc = OxmlElement(tag); fc.set(qn('w:fldCharType'), val); run._r.append(fc)
run.font.name = 'Aptos'; run.font.size = Pt(12)

sec.page_width, sec.page_height = Inches(8.5), Inches(11)
sec.left_margin, sec.right_margin = Cm(4), Cm(3)
sec.top_margin, sec.bottom_margin = Cm(3), Cm(3)
sec.header_distance, sec.footer_distance = Inches(0.5), Inches(0.5)

sectPr = sec._sectPr
tp = OxmlElement('w:titlePg')
sectPr.insert_element_before(tp, 'w:textDirection','w:bidi','w:rtlGather','w:docGrid',
                             'w:printerSettings','w:sectPrChange')
pn = OxmlElement('w:pgNumType'); pn.set(qn('w:start'), '0')
sectPr.insert_element_before(pn, 'w:cols','w:vAlign','w:noEndnote','w:titlePg',
                             'w:textDirection','w:bidi','w:rtlGather','w:docGrid',
                             'w:printerSettings','w:sectPrChange')

for idx, sh in enumerate(d.inline_shapes):
    if idx < len(extents):
        sh.width, sh.height = Emu(extents[idx][0]), Emu(extents[idx][1])

d.save(GEN); shutil.copyfile(GEN, ORIG)
print('docx regenerado:', os.path.getsize(ORIG), 'bytes')
```

⚠️ **No usar `--reference-doc`** con el docx original: incrusta fuentes sin declararlas en
`[Content_Types].xml` y produce un archivo que Word/Python rechazan.

### 6.2 Auditoría de citas IEEE (correr tras cada edición del `.md`)

```bash
python3 - <<'PYEOF'
import re
t = open('Seminario_DanielHernandez_2026.md', encoding='utf8').read()
body, refs = t.split('**Referencias**', 1)
cited = {int(m.group(1)) for m in re.finditer(r'\[(\d+)\]', body)}
defined = {int(x) for x in re.findall(r'^\[(\d+)\]', refs, re.M)}
print("sin citar:", sorted(defined - cited), "| sin definir:", sorted(cited - defined))
first, seen = [], set()
for m in re.finditer(r'\[(\d+)\]', body):
    n = int(m.group(1))
    if n not in seen: seen.add(n); first.append(n)
new = [n for n in first if n >= 19]
print("orden [19+] monótono:", new == sorted(new), "| backslashes:", t.count('\\['))
PYEOF
```
Salida esperada: `sin citar: [] | sin definir: []`, `monótono: True`, `backslashes: 0`.

### 6.3 Referencias verificadas (fuentes consultadas el 14/10/2026)

Todas las nuevas se comprobaron en línea (arXiv/Crossref/URLs 200). Las dudosas resueltas:
Lost in the Middle = Liu et al., *TACL* vol. 12, pp. 157-173, 2024 · Ángles & Gutiérrez,
*ACM Computing Surveys* 40(1):1-39, 2008, **doi:10.1145/1322432.1322433** · BIRD = Li et al.,
NeurIPS 2023 (arXiv:2305.03111) · ReAct (arXiv:2210.03629) · CoT (arXiv:2201.11903) ·
AutoGen (arXiv:2308.08155) · Outlines/Willard & Louf (arXiv:2307.09702) · PagedAttention
(arXiv:2309.06180) · GraphRAG/Edge et al. (arXiv:2404.16130).

## 7. Pendientes (orden sugerido)

1. **Revisar** el Cap. 2 tal como quedó (§3) — el usuario aún no daba su visto bueno final.
2. **Resumen** del documento (vacío).
3. **Índice General** (vacío; ofrecer campo TOC de Word).
4. **Cap. 1:** reescribir para el pipeline de 4 agentes; redactar *Objetivos Específicos*;
   definir el título real del trabajo.
5. **Cap. 3:** metodología/evaluación (no existe).
6. **Cap. 4 — Propuesta de Solución:** integrar `Cap4_Borrador_Tecnologias.md` y renumerar
   las refs [38]-[48] según su posición final.
7. Opcional: renumerar todas las referencias por orden de aparición estricto (tocaría el Cap. 1).
8. Opcional: frase del usuario en Cap. 2 *"En el contexto de esta investigación…"*
   (sección Ventana de contexto) — era candidata a generalizar; el usuario no decidió.

## 8. Preferencias de trabajo del usuario

- Habla inglés/español mezclado; el documento se escribe **en español**.
- Responde bien a preguntas con opciones; pide permiso antes de tocar secciones nuevas.
- **No modificar el Capítulo 1** hasta que él lo indique.
- Formato de cita: **IEEE numerado**, jamás autor-año.
- Solo `.md` versionados; nada de `.docx` en GitHub.
- Quiere avisos cuando haya que cambiar de modo de agente (plan → build) para ejecutar.
