---
title: "GetObject-Funktion (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject-Funktion"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject-Funktion (JavaScript)
Gibt einen Verweis auf ein Automatisierungsobjekt aus einer Datei zurück.  
  
> [!NOTE]
>  Diese Funktion wird in Internet Explorer 9 \(Standardmodus\) oder höher nicht unterstützt.  
  
## Syntax  
  
```  
GetObject([pathname] [, class])  
```  
  
## Parameter  
 `pathname`  
 Dies ist optional.  Der vollständige Pfad und Name der Datei, die das abzurufende Objekt enthält.  Wenn `pathname` nicht angegeben wird, ist `class` erforderlich.  
  
 `class`  
 Dies ist optional.  Klasse des Objekts.  
  
 Das `class`\-Argument verwendet die Syntax `appname.objectype` und verfügt über die folgenden Teile:  
  
 `appname`  
 Erforderlich.  Name der Anwendung, die das Objekt bereitstellt.  
  
 `objectype`  
 Erforderlich.  Typ oder Klasse des zu erstellenden Objekts.  
  
## Hinweise  
 Die `GetObject`\-Funktion wird in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] und höher nicht unterstützt.  
  
 Verwenden Sie die `GetObject`\-Funktion, um auf ein Automatisierungsobjekt aus einer Datei zuzugreifen.  Weisen Sie der Objektvariablen das durch `GetObject` zurückgegebene Objekt zu.  Beispiel:  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Wenn dieser Code ausgeführt wird, wird die in `pathname` angegebene Anwendung gestartet, und das Objekt in der angegebenen Datei wird aktiviert.  Ist `pathname` eine Zeichenfolge mit der Länge 0 \(""\), gibt `GetObject` eine neue Objektinstanz des angegebenen Typs zurück.  Wird das `pathname`\-Argument nicht angegeben, gibt `GetObject` ein gegenwärtig aktives Objekt des angegebenen Typs zurück.  Wenn kein Objekt des angegebenen Typs vorhanden ist, tritt ein Fehler auf.  
  
 Einige Anwendungen bieten die Möglichkeit, eine Datei teilweise zu aktivieren.  Dazu fügen Sie hinter dem Dateinamen ein Ausrufezeichen \(\!\) ein, gefolgt von der Zeichenfolge, die den zu aktivierenden Teil der Datei identifiziert.  Weitere Informationen über das Erstellen dieser Zeichenfolge finden Sie in der Dokumentation der Anwendung, mit der das Objekt erstellt wurde.  
  
 Möglicherweise haben Sie z. B. in einem Zeichenprogramm mehrere Ebenen einer Zeichnung in einer Datei gespeichert.  Mit folgendem Code können Sie eine Ebene in einer Zeichnung mit dem Namen `SCHEMA.CAD` aktivieren:  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Wenn Sie die Objektklasse nicht angeben, bestimmt die Automatisierung anhand des von Ihnen angegebenen Dateinamens, welche Anwendung gestartet und welches Objekt aktiviert wird.  Einige Dateien unterstützen u. U. jedoch auch mehrere Objektklassen.  Eine Zeichnung kann z. B. drei unterschiedliche Objekttypen unterstützen: Ein Anwendungsobjekt, ein Zeichenobjekt und ein Symbolleistenobjekt, die sich alle in derselben Datei befinden.  Um anzugeben, welches Objekt in einer Datei aktiviert werden soll, verwenden Sie das optionale `class`\-Argument.  Beispiel:  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Im vorherigen Beispiel ist `FIGMENT` der Name des Zeichenprogramms, und `DRAWING` ist einer der vom Programm unterstützten Objekttypen.  Sobald ein Objekt aktiviert ist, wird im Code über die definierte Objektvariable darauf verwiesen.  Im vorherigen Beispiel greifen Sie über die `MyObject`\-Objektvariable auf Eigenschaften und Methoden des neuen Objekts zu.  Beispiel:  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Verwenden Sie die `GetObject`\-Funktion, wenn eine aktuelle Instanz des Objekts vorhanden ist oder Sie das Objekt mit einer bereits geladenen Datei erstellen möchten.  Falls keine aktuelle Instanz vorhanden ist und das Objekt nicht mit einer geladenen Datei erstellt werden soll, verwenden Sie das `ActiveXObject`\-Objekt.  
  
 Wenn sich ein Objekt als Einzelinstanzobjekt registriert hat, wird nur eine einzige Instanz dieses Objekts erstellt, unabhängig davon, wie oft `ActiveXObject` ausgeführt wird.  Bei einem Einzelinstanzobjekt gibt `GetObject` bei einem Aufruf mit der Syntax für eine Zeichenfolge der Länge 0 \(""\) stets dieselbe Instanz zurück, und es tritt ein Fehler auf, wenn das `pathname`\-Argument nicht angegeben wird.  
  
## Anforderungen  
 Wird in den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6 \(Standardmodus\), Internet Explorer 7 \(Standardmodus\) und Internet Explorer 8 \(Standardmodus\).  Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## Siehe auch  
 [ActiveXObject\-Objekt](../../javascript/reference/activexobject-object-javascript.md)