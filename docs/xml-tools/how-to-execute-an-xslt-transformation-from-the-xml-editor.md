---
title: Ausführen einer XSLT-Transformation
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fb4aee348ae48a2078f7803a44d4746d3dbacc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668810"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Gewusst wie: Ausführen einer XSLT-Transformation im XML-Editor

Mit dem XML-Editor können Sie einem XML-Dokument ein XSLT-Stylesheet zuordnen, die Transformation ausführen und die Ausgabe anzeigen. Die aus der XSLT-Transformation resultierende Ausgabe wird in einem neuen Dokumentfenster angezeigt.

Die **Output** -Eigenschaft gibt den Dateinamen für die Ausgabe an. Wenn die **Output** -Eigenschaft leer ist, wird ein Dateiname in Ihrem temporären Verzeichnis generiert. Die Dateierweiterung basiert auf dem `xsl:output`-Element im Stylesheet und kann sein. *XML*,. *txt* oder. *htm*.

, Wenn die **Output** -Eigenschaft einen Dateinamen mit einem angibt. *htm* oder. *HTML* -Erweiterung: die XSLT-Ausgabe wird in einem Webbrowser in der Vorschau angezeigt. Alle anderen Dateierweiterungen werden mit dem Standard-Editor geöffnet, der von Visual Studio ausgewählt wird. Wenn die Dateierweiterung beispielsweise ist. *XML*, Visual Studio verwendet den XML-Editor.

## <a name="execute-an-xslt-transformation-from-an-xml-file"></a>Ausführen einer XSLT-Transformation aus einer XML-Datei

1. Öffnen Sie im XML-Editor ein XML-Dokument.

2. Ordnen Sie dem XML-Dokument ein XSLT-Stylesheet zu.

    - Fügen Sie dem XML-Dokument eine `xml-stylesheet`-Verarbeitungsanweisung hinzu. Fügen Sie z. b. die folgende Zeile zum Dokument Prolog hinzu: `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>`

       - oder -

    - Fügen Sie das XSLT-Stylesheet mithilfe des Fensters **Eigenschaften** hinzu. Wenn die XML-Datei im Editor geöffnet ist, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Editor, und wählen Sie **Eigenschaften**. Klicken Sie im Fenster **Eigenschaften** auf das Feld **Stylesheet** , und wählen Sie die Schaltfläche zum Durchsuchen (...) aus. Wählen Sie das XSLT-Stylesheet aus, und wählen Sie dann **Öffnen**aus.

3. Wählen Sie in der Menüleiste die Option **XML**  > **XSLT ohne Debugging starten**aus. Oder drücken Sie **STRG** +**alt** +**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokument Fenster angezeigt.

   > [!NOTE]
   > Wenn dem XML-Dokument kein Stylesheet zugeordnet ist, werden Sie in einem Dialogfeld aufgefordert, das zu verwendende Stylesheet bereitzustellen.

## <a name="execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Ausführen einer XSLT-Transformation aus einem XSLT-Stylesheet

1. Öffnen Sie ein XSLT-Stylesheet im XML-Editor.

2. Geben Sie im Fenster "Dokument **Eigenschaften** " im **Eingabe** Feld ein XML-Dokument an.

   > [!NOTE]
   > Das XML-Dokument ist das für die Transformation verwendete Eingabedokument. Wenn ein Dokument beim Starten der XSLT-Transformation nicht angegeben wird, wird das Dialogfeld **Datei öffnen** angezeigt, und Sie können ein Dokument zu diesem Zeitpunkt angeben.

3. Wählen Sie in der Menüleiste die Option **XML**  > **XSLT ohne Debugging starten**aus. Oder drücken Sie **STRG** +**alt** +**F5**.

   Die Ausgabe der XSLT-Transformation wird in einem neuen Dokument Fenster angezeigt.

## <a name="specify-an-output-file-name"></a>Geben Sie einen Ausgabe Dateinamen an

Sie können sowohl für XML-als auch für XSL-Dateien einen Ausgabe Dateinamen angeben. Öffnen Sie das Fenster **Eigenschaften** , und geben Sie im Feld **Ausgabe** einen Dateinamen an.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)