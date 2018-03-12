---
title: GetObject-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetObject function
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d8bad127a0f260395a1ec19f44ff2d495006024
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getobject-function-javascript"></a>GetObject-Funktion (JavaScript)
Gibt einen Verweis auf ein Automatisierungsobjekt aus einer Datei.  
  
> [!NOTE]
>  Diese Funktion wird nicht in Internet Explorer 9 (Standardmodus) oder höher unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
GetObject([pathname] [, class])  
```  
  
## <a name="parameters"></a>Parameter  
 `pathname`  
 Dies ist optional. Vollständiger Pfad und Name der Datei mit dem Objekt abrufen. Wenn `pathname` weggelassen wird, `class` ist erforderlich.  
  
 `class`  
 Dies ist optional. Die Klasse des Objekts.  
  
 Die `class` Argument verwendet die Syntax `appname.objectype` und besteht aus folgenden Teilen:  
  
 `appname`  
 Erforderlich. Der Name der Anwendung, die das Objekt bereitstellt.  
  
 `objectype`  
 Erforderlich. Typ oder die Klasse des Objekts zu erstellen.  
  
## <a name="remarks"></a>Hinweise  
 Die `GetObject` Funktion wird nicht unterstützt, [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] oder höher.  
  
 Verwenden der `GetObject` Funktion auf ein Automatisierungsobjekt aus einer Datei zuzugreifen. Weisen Sie das zurückgegebene Objekt `GetObject` Objektvariablen. Zum Beispiel:  
  
```JavaScript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 Wenn dieser Code ausgeführt wird, die Anwendung mit dem angegebenen `pathname` gestartet wird, und das Objekt in der angegebenen Datei aktiviert ist. Wenn `pathname` ist eine leere Zeichenfolge (""), `GetObject` gibt eine neue Objektinstanz des angegebenen Typs zurück. Wenn die `pathname` Argument nicht angegeben wird, `GetObject` gibt ein derzeit aktive Objekt des angegebenen Typs zurück. Wenn kein Objekt des angegebenen Typs vorhanden ist, tritt ein Fehler auf.  
  
 Einige Anwendungen können Sie Teil einer Datei zu aktivieren. Zu diesem Zweck fügen Sie am Ende des Dateinamens ein Ausrufezeichen (!), und führen Sie es mit der eine Zeichenfolge, die Teil der Datei identifiziert, die Sie aktivieren möchten. Informationen zum Erstellen dieser Zeichenfolge finden in der Dokumentation für die Anwendung, die das Objekt erstellt.  
  
 Möglicherweise haben in einem Zeichenprogramm mehrere Ebenen einer Zeichnung in einer Datei gespeichert. Können Sie den folgenden Code zum Aktivieren einer Ebene innerhalb einer Zeichnung namens `SCHEMA.CAD`:  
  
```JavaScript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 Wenn Sie die Klasse des Objekts nicht angeben, bestimmt die Automatisierung basierend auf den Dateinamen ein, den Sie bereitstellen, welche die Anwendung gestartet und welches Objekt aktiviert wird. Einige Dateien unterstützen möglicherweise jedoch mehr als eine Klasse des Objekts. Eine Zeichnung könnte z. B. drei verschiedene Typen von Objekten unterstützen: ein Anwendungsobjekt, ein Zeichnungsobjekt und ein Symbolleistenobjekt, die Teil der gleichen Datei sind. Um anzugeben, welches Objekt in einer Datei, die Sie aktivieren möchten, verwenden Sie das optionale `class` Argument. Zum Beispiel:  
  
```JavaScript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 Im vorherigen Beispiel `FIGMENT` ist der Name des eine zeichenanwendung und `DRAWING` ist eines der Objekttypen, die es unterstützt. Sobald ein Objekt aktiviert ist, verweisen Sie ihn im Code mithilfe von Object-Variablen, die Sie definiert. Im vorherigen Beispiel aus, den Sie Eigenschaften und Methoden des neuen Objekts, wobei die Objektvariable zugreifen `MyObject`. Zum Beispiel:  
  
```JavaScript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  Verwenden der `GetObject` -Funktion, wenn eine aktuelle Instanz des Objekts vorhanden ist oder wenn Sie möchten, zum Erstellen des Objekts mit eine Datei bereits geladen. Wenn keine aktuelle Instanz vorhanden ist und Sie möchten schließlich nicht das Objekt mit eine Datei geladen wurde, verwenden Sie die `ActiveXObject` Objekt.  
  
 Wenn ein Objekt als ein Einzelinstanz-Objekt registriert hat, nur eine Instanz des Objekts wird erstellt, unabhängig davon, wie oft `ActiveXObject` ausgeführt wird. Bei einem Einzelinstanz-Objekt `GetObject` immer die gleiche Instanz bei einem Aufruf mit der Zeichenfolge der Länge 0 (null) zurück ("")-Syntax, und es tritt einen Fehler auf, wenn die `pathname` Argument nicht angegeben wird.  
  
## <a name="requirements"></a>Anforderungen  
 In den folgenden Dokumentmodi unterstützt: Quirksmodus, Internet Explorer 6-Standardmodus, Internet Explorer 7-Standardmodus und Internet Explorer 8 (Standardmodus). Siehe [Versionsinformationen](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ActiveXObject-Objekt](../../javascript/reference/activexobject-object-javascript.md)