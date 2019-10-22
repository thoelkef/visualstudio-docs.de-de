---
title: XML-Dokumenteigenschaften, Eigenschaften Fenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669515"
---
# <a name="xml-document-properties-properties-window"></a>XML-Dokumenteigenschaften, Eigenschaftenfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster **Eigenschaften** enthält grundlegende Informationen über das Dokument, das im XML-Editor aktiv ist. Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML-Dokuments abhängig.

> [!NOTE]
> Alle XML-Dokumenteigenschaften werden in der Projektmappe gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

 **Codierung** Die Zeichencodierung für die Datei. Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML-Deklaration geändert und umgekehrt. Die neue Codierung wird beim Speichern der Datei zum Codieren der Datei verwendet.

 **Eingabe** Das Eingabe Dokument, das dem XSLT-Stylesheet zugeordnet ist. Sie wird vom Befehl " **ShowXSLT Output** " verwendet. Ein Dokument kann mithilfe der Schaltfläche zum Durchsuchen ( **...** ) ausgewählt werden.

 Diese Eigenschaft ist nur sichtbar, wenn derzeit eine XSLT-Datei im Editor-Fenster aktiv ist.

 **Ausgabe** Die Datei, die beim Transformieren eines XML-Dokuments generiert wird.

 Wenn keine Datei angegeben wurde, wird aufgrund des `method`-Attributs für das `xsl:output`-Element, das die Dateierweiterung festlegt, ein Standarddateiname generiert. Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.

 **Schemas** Die Schemas, die für die Validierung verwendet werden sollen. Mit der Schaltfläche wird das Dialogfeld **XSD-Schemas** geöffnet, in dem die zu verwendenden Schemas ausgewählt werden können.

 Sie können den Pfad zu den Schemata auch eingeben. Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.

 **Stylesheet** Die XSLT-Datei, die verwendet wird, um das Dokument zu transformieren, wenn der Befehl " **XSLT-Ausgabe anzeigen** " verwendet wird. Wenn dieses Feld leer ist, wenn der Befehl **XSLT-Ausgabe anzeigen** verwendet wird, verwendet der Editor den Wert, der in der `xml-stylesheet` Verarbeitungsanweisung des Dokuments bereitgestellt wird, oder Sie werden zur Eingabe des Datei namens aufgefordert.

 Wenn Sie eine XSLT-Datei bearbeiten, kann diese Eigenschaft verwendet werden, um anzugeben, dass ein anderes Stylesheet verwendet werden soll, wenn der Befehl **XSLT-Ausgabe anzeigen** oder **XSLT Debuggen** ausgewählt ist. Dies kann z. B. beim Bearbeiten eines Stylesheets der Fall sein, das in einem übergeordneten Stylesheet enthalten ist.

## <a name="see-also"></a>Siehe auch
 XML-Editor- [Komponenten](../xml-tools/xml-editor-components.md) in [XML](../xml-tools/xml-editor.md)
