---
title: "XML-Dokumenteigenschaften, Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML-Dokumenteigenschaften, Eigenschaftenfenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Eigenschaftenfenster liefert grundlegende Informationen zu dem im XML\-Editor aktiven Dokument.Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML\-Dokuments abhängig.  
  
> [!NOTE]
>  Alle XML\-Dokumenteigenschaften werden in der Projektmappe gespeichert.Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.  
  
 **Codierung**  
 Die Zeichencodierung für die Datei.Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML\-Deklaration geändert und umgekehrt.Die neue Codierung wird beim Speichern der Datei zum Codieren der Datei verwendet.  
  
 **Eingabe**  
 Das dem XSLT\-Stylesheet zugeordnete Eingabedokument.Es wird bei dem Befehl **XSLT\-Ausgabe anzeigen** verwendet.Mit der Schaltfläche zum Durchsuchen \(**...**\) kann ein Dokument ausgewählt werden.  
  
 Diese Eigenschaft ist nur sichtbar, wenn derzeit eine XSLT\-Datei im Editor\-Fenster aktiv ist.  
  
 **Ausgabe**  
 Die bei der Transformation eines XML\-Dokuments generierte Datei.  
  
 Wenn keine Datei angegeben wurde, wird aufgrund des `method`\-Attributs für das `xsl:output`\-Element, das die Dateierweiterung festlegt, ein Standarddateiname generiert.Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.  
  
 **Schemata**  
 Die für die Validierung verwendeten Schemata.Die Schaltfläche öffnet das Dialogfeld **XSD\-Schemata**, womit die zu verwendenden Schemata ausgewählt werden können.  
  
 Sie können den Pfad zu den Schemata auch eingeben.Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.  
  
 **Stylesheet**  
 Die XSLT\-Datei, die zum Transformieren des Dokuments mit dem Befehl **XSLT\-Ausgabe anzeigen** verwendet wird.Wenn dieses Feld bei Verwendung des Befehls **XSLT\-Ausgabe anzeigen** leer ist, verwendet der Editor den in der `xml-stylesheet`\-Verarbeitungsanweisung des Dokuments angegebenen Wert, oder Sie werden zum Eingeben des Dateinamens aufgefordert.  
  
 Beim Bearbeiten einer XSLT\-Datei kann mithilfe dieser Eigenschaft angegeben werden, dass ein anderes Stylesheet verwendet werden soll, wenn der Befehl **XSLT\-Ausgabe anzeigen** oder **XSLT debuggen** ausgewählt wurde.Dies kann z. B. beim Bearbeiten eines Stylesheets der Fall sein, das in einem übergeordneten Stylesheet enthalten ist.  
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)   
 [Komponenten des XML\-Editors](../xml-tools/xml-editor-components.md)