---
title: "Anweisungsvervollst&#228;ndigung f&#252;r Bezeichner | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [JavaScript], Anweisungsvervollständigung"
  - "Anweisungsvervollständigung, JavaScript IntelliSense"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Anweisungsvervollst&#228;ndigung f&#252;r Bezeichner
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript lässt keine explizite Variablendeklarationen eingeben.  Infolgedessen kann nicht IntelliSense immer Vervollständigungslisten für Objekte bereitzustellen.  Dies kann in verschiedenen Situationen auftreten.  Im folgenden werden einige häufigsten Gründe.  
  
-   Ein Parameter deklariert ist, aber es wurde nicht aufgerufen an anderer Stelle im aktiven Dokument, wie im folgenden Beispiel gezeigt.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Ein Objekt ist in einer Funktion, die in Reaktion auf ein Ereignis aufgerufen wird.  IntelliSense\-Engine kann nicht den Typ der Objekte in dieser Situation bestimmen, zur Entwurfszeit.  
  
     Wenn die IntelliSense\-Engine bestimmen kann, dass das Ereignis, in der Regel durch die Verwendung von aufgerufen werden muss, `addEventListener` für das Ereignis im aktiven Dokument, eine genauere IntelliSense Informationen.  
  
 Wenn IntelliSense nicht in der Lage, ein Objekt zu identifizieren ist, füllt die IntelliSense\-Engine die Vervollständigungsliste mit benannten Entitäten oder Identifier definiert, die im aktiven Dokument vorhanden sind.  Wenn die Vervollständigungsliste diese Bezeichner enthält, werden Symbole gekennzeichnet.  Darüber hinaus gibt eine QuickInfo für jeden Bezeichner an, dass der Ausdruck unbekannt ist.  Die folgende Abbildung zeigt Anweisung Abschlussoptionen für ein Objekt vom Typ `light` , die nicht ermittelt werden, da das Objekt und seine Eigenschaften nicht definiert sind.  Jedoch die `intensity` Eigenschaft ist in der Liste Organisationskennzeichen verfügbar, da es in verwendet wurde die `illuminate` Funktion.  
  
 **Ausführungsoptionen für ein Objekt, das nicht identifiziert werden können**  
  
 ![JavaScript IntelliSense für Bezeichner](~/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 Sie können die Vervollständigungsliste für ein Objekt mithilfe von XML\-Dokumentationskommentare oder JavaScript\-IntelliSense\-Erweiterungsfeatures überschreiben.  Mithilfe dieser Features können bietet Sie Typinformationen und weitere beschreibende Informationen für IntelliSense, wenn es sonst möglicherweise nicht verfügbar.  Weitere Informationen finden Sie unter [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) und [Gewusst wie: Erstellen von JavaScript\-XML\-Dokumentationskommentaren](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## Siehe auch  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)