<!DOCTYPE html>
<html>
<body>
<h4>Convertir grafos de <a href="https://graphonline.ru/es/" target="_blank">graphonline.ru</a> a lista de tuplas de 3 elementos para el TP de Introducción a la Programación</h4>
<h4>Copyright (C) 2024 Gabriel Faeda</h4>

<h4>Instrucciones:</h4>
<p>1 - En graphonline.ru ir a graph->export to file y guardar el archivo *.graphml</p>
<p>2 - Abrir el archivo con el bloc de notas y copiar el código en el cuadro de texto superior de esta página</p>
<p>3 - Hacer clic en Procesar y el código se convertirá en una lista de tuplas de tres elementos de Haskell que aparecerá en el cuadro de texto inferior.</p>
<p></p>
<p>Nota: Solo funciona para grafos dirigidos</p>
<br>
<p>Codigo XML</p>
<textarea id="show_input" name="input" rows="4" cols="50">
</textarea>
</p><button onclick="processGraphsXML()">Procesar</button> </p>
<br>
<p>Tupla triple de Haskell</p>
<textarea id="show_result" name="output" rows="4" cols="50">
</textarea>

<script>

var parser, xmlDoc;

parser = new DOMParser();
function processGraphsXML(){
  xmlDoc = parser.parseFromString(document.getElementById("show_input").value,"text/xml");

  var allNames = xmlDoc.getElementsByTagName("node");
  var allPaths = xmlDoc.getElementsByTagName("edge");
  document.getElementById("show_result").value = "[";
  for(i = 0; i < allPaths.length; i++){
      document.getElementById("show_result").value = document.getElementById("show_result").value + '("' + allNames[parseInt(allPaths[i].getAttribute("source"))].getAttribute("mainText") + '", "' + allNames[parseInt(allPaths[i].getAttribute("target"))].getAttribute("mainText") + '", ' + allPaths[i].getAttribute("weight") + ".0)";
      if(i < allPaths.length - 1){
          document.getElementById("show_result").value = document.getElementById("show_result").value + ","
      }
  }
  document.getElementById("show_result").value = document.getElementById("show_result").value + "]";
  }
</script>

</body>
</html>
