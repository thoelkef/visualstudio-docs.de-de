---
title: Ausführen einer XSLT-transformation
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84b1c6303da4c0db39da1b3585a7d4548560feb
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526372"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Vorgehensweise: Ausführen einer XSLT-Transformations im XML-Editor

Der XML-Editor können Sie ein XML-Dokument eine XSLT-Stylesheet zuordnen, die Transformation ausführen und Anzeigen der Ausgabe. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

Die **Ausgabe** Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Ausgabe** -Eigenschaft leer ist, ein Dateinamen in einem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf der `xsl:output` -Element im Stylesheet and kann. *XML*,. *TXT* oder. *Htm*.

Wenn die **Ausgabe** Eigenschaft gibt einen Dateinamen mit einer. *Htm* oder. *HTML* Erweiterung der XSLT-Ausgabe wird in der Vorschau angezeigten mithilfe eines Webbrowsers. Allen anderen Dateierweiterungen werden geöffnet, mit dem Standardeditor von Visual Studio ausgewählt. Wenn beispielsweise die Dateierweiterung ist. *Xml*, verwendet den XML-Editor von Visual Studio.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ausführen einer XSLT-Transformation eine XML-Datei

1. Öffnen Sie ein XML-Dokument, in der XML-Editor.

2. Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    - Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Dokumentprolog z. B. die folgende Zeile hinzugefügt: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       - oder - 

    - Fügen Sie dem XSLT-Stylesheet mithilfe der **Eigenschaften** Fenster. Klicken Sie mit der XML-Datei im Editor geöffnet, mit der rechten Maustaste an einer beliebigen Stelle im Editor, und wählen Sie **Eigenschaften**. In der **Eigenschaften** Fenster, klicken Sie in der **Stylesheet** Feld, und wählen Sie die Schaltfläche zum Durchsuchen (...). Wählen Sie das XSLT-Stylesheet, und wählen Sie dann **öffnen**.

3. Wählen Sie auf der Menüleiste **XML** > **XSLT ohne Debugging starten**. Oder drücken Sie **STRG**+**Alt**+**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokumentfenster angezeigt.

   > [!NOTE]
   > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ausführen einer XSLT-Transformation ein XSLT-Stylesheet

1. Öffnen Sie eine XSLT-Stylesheet im XML-Editor ein.

2. Geben Sie eine XML-Dokument in der **Eingabe** Feld des Dokuments **Eigenschaften** Fenster.

   > [!NOTE]
   > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument nicht angegeben wird, wenn die XSLT-Transformation gestartet wird, die **Datei öffnen** Dialogfeld wird angezeigt, und Sie können ein Dokument zu diesem Zeitpunkt angeben.

3. Wählen Sie auf der Menüleiste **XML** > **XSLT ohne Debugging starten**. Oder drücken Sie **STRG**+**Alt**+**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokumentfenster angezeigt.

## <a name="specify-an-output-file-name"></a>Geben Sie einen Ausgabedateinamen

Sie können ein Ausgabedateiname für XML und XSL-Dateien angeben. Öffnen der **Eigenschaften** Fenster, und geben Sie einen Namen in der **Ausgabe** Feld.

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)