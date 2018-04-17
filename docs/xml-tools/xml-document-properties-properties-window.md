---
title: XML-Dokumenteigenschaften, Eigenschaftenfenster | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d6529d936515c23c193a38861f1f13b71002566
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xml-document-properties-properties-window"></a>XML-Dokumenteigenschaften, Eigenschaftenfenster
Die **Eigenschaften** Fenster enthält grundlegende Informationen über das Dokument, das in der XML-Editor aktiv ist. Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML-Dokuments abhängig.  
  
> [!NOTE]
>  Alle XML-Dokumenteigenschaften werden in der Projektmappe gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.  
  
 **Codierung**  
 Die Zeichencodierung für die Datei. Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML-Deklaration geändert und umgekehrt. Die neue Codierung wird beim Speichern der Datei zum Codieren der Datei verwendet.  
  
 **Eingabe**  
 Das dem XSLT-Stylesheet zugeordnete Eingabedokument. Es dient der **ShowXSLT Ausgabe** Befehl. Ein Dokument kann ausgewählt werden, verwenden die Schaltfläche zum Durchsuchen (**...** ) Schaltfläche.  
  
 Diese Eigenschaft ist nur sichtbar, wenn derzeit eine XSLT-Datei im Editor-Fenster aktiv ist.  
  
 **Ausgabe**  
 Die bei der Transformation eines XML-Dokuments generierte Datei.  
  
 Wenn keine Datei angegeben wurde, wird aufgrund des `method`-Attributs für das `xsl:output`-Element, das die Dateierweiterung festlegt, ein Standarddateiname generiert. Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.  
  
 **Schemas**  
 Die für die Validierung verwendeten Schemata. Die Schaltfläche öffnet die **XSD-Schemas** im Dialogfeld zum Auswählen der zu verwendenden Schemas verwendet werden kann.  
  
 Sie können den Pfad zu den Schemata auch eingeben. Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.  
  
 **Stylesheet**  
 Die XSLT-Datei, die verwendet wird, um das Dokument zu transformieren bei der **XSLT-Ausgabe anzeigen** -Befehl verwendet wird. Sollte dieses Feld leer bei der **XSLT-Ausgabe anzeigen** Befehl verwendet wird, den der Editor verwendet die angegebene Wert der `xml-stylesheet` -verarbeitungsanweisung des Dokuments oder es fordert Sie zum Eingeben des Dateinamens.  
  
 Wenn Sie eine XSLT-Datei bearbeiten, kann diese Eigenschaft verwendet werden, um anzugeben, dass ein anderes Stylesheet werden sollte verwendet werden, wenn die **XSLT-Ausgabe anzeigen** oder **XSLT Debuggen** Befehl ausgewählt ist. Dies kann z. B. beim Bearbeiten eines Stylesheets der Fall sein, das in einem übergeordneten Stylesheet enthalten ist.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)   
 [Komponenten des XML-Editors](../xml-tools/xml-editor-components.md)