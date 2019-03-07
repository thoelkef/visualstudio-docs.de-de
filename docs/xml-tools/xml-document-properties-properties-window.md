---
title: XML-Dokumenteigenschaften, Eigenschaftenfenster
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526268"
---
# <a name="xml-document-properties-properties-window"></a>XML-Dokumenteigenschaften, Eigenschaftenfenster

Die **Eigenschaften** Eigenschaftenfenster liefert grundlegende Informationen über das Dokument, das in der XML-Editor aktiv ist. Die verfügbaren Eigenschaften sind vom Typ des gerade aktiven XML-Dokuments abhängig.

> [!NOTE]
> Alle XML-Dokumenteigenschaften werden in der Projektmappe gespeichert. Dadurch müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

**Encoding**

Die Zeichencodierung für die Datei. Wenn diese Eigenschaft geändert wird, wird auch das Codierungsattribut für die XML-Deklaration geändert und umgekehrt. Die neue Codierung wird verwendet, um die Datei zu codieren, wenn Sie die Datei speichern.

**Eingabe**

Das dem XSLT-Stylesheet zugeordnete Eingabedokument. Es dient der **XSLT starten** Befehle, z. B. **XML** > **XSLT ohne Debugging starten**. Ein Dokument mit der Schaltfläche ausgewählt werden kann (**...** ) Schaltfläche.

Diese Eigenschaft wird angezeigt, nur, wenn eine XSLT-Datei im Editor geöffnet ist.

**Ausgabe**

Die bei der Transformation eines XML-Dokuments generierte Datei.

Wenn eine Datei nicht angegeben ist, ein Standarddateiname wird generiert basierend auf den `method` -Attribut für die `xsl:output` -Element, das die Dateierweiterung bestimmt. Die Standarddatei befindet sich im temporären Verzeichnis des aktuellen Benutzers.

**Schemas**

Die für die Validierung verwendeten Schemata. Die Schaltfläche öffnet die **XSD-Schemas** das Dialogfeld zum Auswählen der zu verwendenden Schemas verwendet werden kann.

Sie können den Pfad zu den Schemata auch eingeben. Wenn mehrere Schemata angegeben sind, muss jeder Schemapfad in doppelte Anführungszeichen eingeschlossen werden.

**Stylesheet**

Die XSLT-Datei, die verwendet wird, um das Dokument zu transformieren. wenn die **XSLT Debuggen starten** und **XSLT ohne Debugging starten** -Befehle verwendet werden. Wenn dieses Feld leer ist, wird der Editor verwendet den Wert der `xml-stylesheet` -verarbeitungsanweisung des Dokuments oder es fordert Sie zur Eingabe eines Dateinamens.

Beim Bearbeiten einer XSLT-Datei kann diese Eigenschaft verwendet werden, um anzugeben, dass ein anderes Stylesheet sollte verwendet werden, wenn die **XSLT Debuggen starten** oder **XSLT ohne Debugging starten** Befehl aktiviert ist. Beispielsweise empfiehlt es sich um dies zu tun, wenn Sie ein Stylesheet bearbeiten, die in einem übergeordneten Stylesheet enthalten ist.

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)