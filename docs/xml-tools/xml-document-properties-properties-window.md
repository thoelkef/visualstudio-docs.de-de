---
title: XML-Dokumenteigenschaften, Eigenschaftenfenster
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99102248a9456de3a2b3aeba28e54de4299fae40
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604159"
---
# <a name="xml-document-properties-properties-window"></a>XML-Dokumenteigenschaften, Eigenschaftenfenster

Das Fenster **Eigenschaften** enthält grundlegende Informationen über das Dokument, das im XML-Editor aktiv ist. Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML-Dokuments abhängig.

> [!NOTE]
> Alle XML-Dokumenteigenschaften werden in der Projektmappe gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

**Kodierung**

Die Zeichencodierung für die Datei. Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML-Deklaration geändert und umgekehrt. Die neue Codierung wird verwendet, um die Datei zu codieren, wenn Sie die Datei speichern.

**Eingabe**

Das dem XSLT-Stylesheet zugeordnete Eingabedokument. Sie wird von den **Start-XSLT** -Befehlen verwendet, z. b. **XML**  > **XSLT ohne Debugging starten**. Ein Dokument kann mithilfe der Schaltfläche zum Durchsuchen ( **...** ) ausgewählt werden.

Diese Eigenschaft ist nur sichtbar, wenn eine XSLT-Datei im Editor geöffnet ist.

**Ausgabe**

Die bei der Transformation eines XML-Dokuments generierte Datei.

Wenn keine Datei angegeben wird, wird ein Standard Dateiname basierend auf dem `method`-Attribut im `xsl:output`-Element generiert, das die Dateierweiterung bestimmt. Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.

**Schemas**

Die für die Validierung verwendeten Schemata. Mit der Schaltfläche wird das Dialogfeld **XSD-Schemas** geöffnet, in dem die zu verwendenden Schemas ausgewählt werden können.

Sie können den Pfad zu den Schemata auch eingeben. Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.

**Stylesheet**

Die XSLT-Datei, die verwendet wird, um das Dokument zu transformieren, wenn die Befehle **XSLT-Debugging starten** und **XSLT ohne Debugging** starten verwendet werden. Wenn dieses Feld leer ist, verwendet der Editor den Wert, der in der `xml-stylesheet` Verarbeitungsanweisung des Dokuments enthalten ist, oder Sie werden aufgefordert, einen Dateinamen einzugeben.

Wenn Sie eine XSLT-Datei bearbeiten, kann diese Eigenschaft verwendet werden, um anzugeben, dass ein anderes Stylesheet verwendet werden soll, wenn der Befehl **XSLT-Debugging starten** oder **XSLT ohne Debugging** starten ausgewählt ist. Dies kann z. b. der Fall sein, wenn Sie ein Stylesheet bearbeiten, das in einem übergeordneten Stylesheet enthalten ist.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)