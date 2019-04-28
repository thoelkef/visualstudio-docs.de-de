---
title: Debuggen von XSLT-Stylesheets
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808473"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets

Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT-Debuggers veranschaulicht. Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes. Der Debugger können Sie den Code zeilenweise ausführen.

Um für diese exemplarische Vorgehensweise vorzubereiten, kopieren Sie zunächst die beiden [Beispieldateien](#sample-files) auf dem lokalen Computer. Eine ist das Stylesheet, und eine ist die XML-Datei, die wir als Eingabe für das Stylesheet verwenden werden. In dieser exemplarischen Vorgehensweise ist sucht das Stylesheet, die, das wir verwenden, alle Bücher, deren Kosten unter der durchschnittliche Buchpreis liegt.

> [!NOTE]
> Der XSLT-Debugger ist nur verfügbar, in der Enterprise Edition von Visual Studio.

## <a name="start-debugging"></a>Debugging starten

1. Von der **Datei** Menü wählen **öffnen** > **Datei**.

2. Suchen Sie die *unten average.xsl* Datei, und wählen **öffnen**.

   Das Stylesheet wird in der XML-Editor geöffnet.

3. Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Eingabe** Eigenschaftenfenster des Dokuments im Feld. (Wenn die **Eigenschaften** Fenster ist nicht sichtbar, mit der rechten Maustaste auf die geöffnete Datei im Editor, und wählen Sie dann **Eigenschaften**.)

4. Suchen Sie die *books.xml* Datei, und wählen Sie dann **öffnen**.

   Hiermit wird die Quelldatei für das Dokument, die für die XSLT-Transformation verwendet wird.

5. Legen Sie eine [Haltepunkt](../debugger/using-breakpoints.md) in Zeile 12 des *unten average.xsl*. Sie können in vielfältigen Möglichkeiten dazu:

   - Klicken Sie auf den Rand des Editors in Zeile 12.

   - Klicken Sie auf eine beliebige Stelle in Zeile 12, und drücken Sie dann die **F9**.

   - Mit der rechten Maustaste die `xsl:if` Starttag, und wählen Sie dann **Haltepunkt** > **Haltepunkt einfügen**.

      ![Haltepunkt in XSL-Datei in Visual Studio einfügen](media/insert-breakpoint.PNG)

6. Wählen Sie auf der Menüleiste **XML** > **XSLT Debuggen starten** (oder drücken Sie **Alt**+**F5**).

   Der Debug-Vorgang wird gestartet.

   Im Editor befindet sich der Debugger auf dem `xsl:if` -Element des Stylesheets. Eine andere Datei, die mit dem Namen *unten average.xml* öffnet im Editor; Dies ist die Ausgabedatei, die als einzelnen Knoten in der Eingabedatei aufgefüllt wird *books.xml* verarbeitet wird.

   Die **"Auto"**, **"lokal"**, und **Überwachen 1** Fenster am unteren Rand des Fensters von Visual Studio angezeigt werden. Die **"lokal"** Fenster zeigt alle lokalen Variablen und ihre aktuellen Werte. Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.

## <a name="watch-window"></a>Überwachungsfenster

Wir fügen zwei Variablen auf die **Überwachen 1** Fenster, damit wir ihre Werte untersuchen können, wenn die Eingabedatei verarbeitet werden. (Sie können auch die **"lokal"** Fenster aus, um Werte zu überprüfen, wenn die Variablen, die Sie überwachen möchten bereits vorhanden sind.)

1. Aus der **Debuggen** Menü wählen **Windows** > **Watch** > **Überwachen 1**.

   Die **Überwachen 1** Fenster wird angezeigt.

2. Typ `$bookAverage` in die **Namen** Feld, und drücken Sie dann die **EINGABETASTE**.

   Der Wert des der `$bookAverage` Variablen zeigt, in der **Wert** Feld.

3. Geben Sie auf der nächsten Zeile `self::node()` in die **Namen** Feld, und drücken Sie dann die **EINGABETASTE**.

   `self::node()` ist ein XPath-Ausdruck, der den aktuellen Kontextknoten auswertet. Der Wert des `self::node()`-XPath-Ausdrucks ist der erste book-Knoten. Dieser ändert sich im Laufe der Transformation.

4. Erweitern Sie die `self::node()` Knoten, und klicken Sie dann den Knoten, die hat Wert `price`.

   ![Fenster "überwachen", während der XSLT-Debuggen in Visual Studio](media/xslt-debugging-watch-window.png)

   Sie können finden Sie unter den Wert des Buchpreises für den aktuellen Buchknoten, und vergleichen Sie ihn mit der `$bookAverage` Wert. Da der Buchpreis unterhalb des Durchschnitts, ist die `xsl:if` Bedingung sollte erfolgreich sein, wenn Sie den Debugvorgang fortsetzen.

## <a name="step-through-the-code"></a>Den Code schrittweise durchgehen

1. Drücken Sie **F5**, um fortzufahren.

   Da der erste Buchknoten erfüllt die `xsl:if` Bedingung, dem-Knoten hinzugefügt wird die *unten average.xml* Ausgabedatei. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich nun auf dem zweiten Book-Knoten in der *books.xml* Datei.

   In der **Überwachen 1** Fenster die `self::node()` Wert ändert sich in der zweiten Buchknoten. Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`-Bedingung fehlschlägt.

2. Drücken Sie **F5**, um fortzufahren.

   Da der zweite Buchknoten nicht erfüllt die `xsl:if` Bedingung der Buchknoten wird nicht hinzugefügt der *unten average.xml* Ausgabedatei. Der Debugger wird weiterhin ausgeführt, bis es wieder auf positioniert ist die `xsl:if` -Element im Stylesheet. Der Debugger befindet sich jetzt am dritten `book` Knoten in der *books.xml* Datei.

   In der **Überwachen 1** Fenster die `self::node()` Wert ändert sich in der dritten Buchknoten. Durch die Auswertung des Werts für die `price` Element können Sie feststellen, dass der Preis unter dem Durchschnitt ist. Die `xsl:if` -Bedingung erfüllt ist.

3. Drücken Sie **F5**, um fortzufahren.

   Da die `xsl:if` -Bedingung erfüllt war, das dritte Buch wird hinzugefügt die *unten average.xml* Ausgabedatei. Alle Bücher im XML-Dokument wurden verarbeitet, und der Debugger wird beendet.

## <a name="sample-files"></a>Beispieldateien

Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.

### <a name="below-averagexsl"></a>below-average.xsl

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

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)