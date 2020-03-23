---
title: Debuggen von XSLT-Stylesheets
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79300942"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets

Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT-Debuggers veranschaulicht. Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes. Mit dem Debugger können Sie Code jeweils eine Zeile ausführen.

Um sich auf diese exemplarische Vorgehensweise vorzubereiten, kopieren Sie zunächst die beiden [Beispieldateien](#sample-files) auf Ihren lokalen Computer. Eines davon ist das Stylesheet, und eines ist die XML-Datei, die wir als Eingabe für das Stylesheet verwenden. In dieser exemplarischen Vorgehensweise findet das Stylesheet, das wir verwenden, alle Bücher, deren Kosten unter dem durchschnittlichen Buchpreis liegen.

> [!NOTE]
> Der XSLT-Debugger ist nur in der Enterprise-Edition von Visual Studio verfügbar.

## <a name="start-debugging"></a>Starten des Debugvorgangs

1. Wählen Sie im Menü **Datei** **die**Option Datei **öffnen** > aus.

2. Suchen Sie die *unterdurchschnittliche.xsl-Datei* und wählen Sie **Öffnen**.

   Das Stylesheet wird im XML-Editor geöffnet.

3. Klicken Sie im **Eingabefeld** des Dokumenteigenschaftenfensters auf die Schaltfläche "Durchsuchen" (**...**). (Wenn das **Eigenschaftenfenster** nicht sichtbar ist, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in der geöffneten Datei im Editor, und wählen Sie dann **Eigenschaften**aus .)

4. Suchen Sie die Datei *books.xml,* und wählen Sie dann **Öffnen**aus.

   Dadurch wird die Quelldokumentdatei festgelegt, die für die XSLT-Transformation verwendet wird.

5. Legen Sie einen [Haltepunkt](../debugger/using-breakpoints.md) in Zeile 12 von *unterdurchschnittlich.xsl*fest. Sie können dies auf eine von mehreren Arten tun:

   - Klicken Sie in den Rand des Editors in Zeile 12.

   - Klicken Sie auf eine beliebige Stelle in Zeile 12, und drücken Sie dann **F9**.

   - Klicken Sie `xsl:if` mit der rechten Maustaste auf das Starttag, und wählen Sie dann **Breakpoint** > **Insert Breakpoint**aus.

      ![Einfügen eines Haltepunkts in die XSL-Datei in Visual Studio](media/insert-breakpoint.PNG)

6. Wählen Sie in der Menüleiste **XML** > **Start XSLT Debugging** (oder drücken Sie **Alt**+**F5**).

   Der Debugvorgang wird gestartet.

   Im Editor wird der Debugger `xsl:if` auf dem Element des Stylesheets positioniert. Eine andere Datei mit dem Namen *unter durchschnittlich.xml* wird im Editor geöffnet. Dies ist die Ausgabedatei, die als jeder Knoten in der Eingabedatei *books.xml* aufgefüllt wird.

   Die Fenster **Autos**, **Locals**und **Watch 1** werden am unteren Rand des Visual Studio-Fensters angezeigt. Im Fenster **Locals** werden alle lokalen Variablen und ihre aktuellen Werte angezeigt. Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.

## <a name="watch-window"></a>Überwachungsfenster

Wir fügen dem Watch **1-Fenster** zwei Variablen hinzu, damit wir deren Werte untersuchen können, während die Eingabedatei verarbeitet wird. (Sie können auch das Fenster **Locals** verwenden, um Werte zu untersuchen, wenn die Variablen, die Sie ansehen möchten, bereits vorhanden sind.)

1. Wählen Sie im **Menü Debugdier** **Windows** > **Watch** > Watch**1**aus.

   Das **Uhr-1-Fenster** wird sichtbar.

2. Geben `$bookAverage` Sie das Feld **Name** ein, und drücken Sie dann **die Eingabetaste**.

   Der Wert `$bookAverage` der Variablen wird im Feld **Wert** angezeigt.

3. Geben Sie `self::node()` in der nächsten Zeile das Feld **Name** ein, und drücken Sie dann **die Eingabetaste**.

   `self::node()`ist ein XPath-Ausdruck, der zum aktuellen Kontextknoten ausgewertet wird. Der Wert des -XPath-Ausdrucks ist der erste book-Knoten. Dieser ändert sich im Laufe der Transformation.

4. Erweitern `self::node()` Sie den Knoten, und erweitern Sie `price`dann den Knoten, dessen Wert ist.

   ![Überwachungsfenster beim XSLT-Debuggen in Visual Studio](media/xslt-debugging-watch-window.png)

   Sie können den Wert des Buchpreises für den aktuellen `$bookAverage` Buchknoten anzeigen und mit dem Wert vergleichen. Da der Buchpreis unter dem `xsl:if` Durchschnitt liegt, sollte die Bedingung erfolgreich sein, wenn Sie den Debugvorgang fortsetzen.

## <a name="step-through-the-code"></a>Schritt durch den Code

1. Drücken Sie **F5,** um fortzufahren.

   Da der erste Buchknoten die `xsl:if` Bedingung erfüllt, wird der Buchknoten der *Ausgabedatei unter durchschnittlich.xml* hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger wird nun auf dem zweiten Buchknoten in der Datei *books.xml* positioniert.

   Im Fenster **Watch** 1 `self::node()` ändert sich der Wert in den zweiten Buchknoten. Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`-Bedingung fehlschlägt.

2. Drücken Sie **F5,** um fortzufahren.

   Da der zweite Buchknoten `xsl:if` die Bedingung nicht erfüllt, wird der Buchknoten nicht zur *Ausgabedatei unter durchschnittlich.xml* hinzugefügt. Der Debugger wird so lange ausgeführt, `xsl:if` bis er wieder auf dem Element im Stylesheet positioniert ist. Der Debugger befindet sich `book` nun auf dem dritten Knoten in der Datei *books.xml.*

   Im Fenster **Watch** 1 `self::node()` ändert sich der Wert in den dritten Buchknoten. Wenn Sie den `price` Wert des Elements untersuchen, können Sie feststellen, dass der Preis unter dem Durchschnitt liegt. Die `xsl:if` Bedingung sollte erfolgreich sein.

3. Drücken Sie **F5,** um fortzufahren.

   Da `xsl:if` die Bedingung erfüllt war, wird das dritte Buch der *Ausgabedatei unter durchschnittlich.xml* hinzugefügt. Alle Bücher im XML-Dokument wurden verarbeitet, und der Debugger wird beendet.

## <a name="sample-files"></a>Beispieldateien

Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.

### <a name="below-averagexsl"></a>unterdurchschnittlich.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Weitere Informationen

- [Debugging von XSLT](../xml-tools/debugging-xslt.md)
