---
title: XSLT-Stylesheets debuggen
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410117"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets

Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT-Debuggers veranschaulicht. Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes. Mit dem Debugger können Sie Codezeilen Weise ausführen.

Um diese exemplarische Vorgehensweise vorzubereiten, kopieren Sie zunächst die beiden [Beispieldateien](#sample-files) auf Ihren lokalen Computer. Eine ist das Stylesheet, und eine ist die XML-Datei, die wir als Eingabe für das Stylesheet verwenden. In dieser exemplarischen Vorgehensweise findet das verwendete Stylesheet alle Bücher, deren Kosten unter dem durchschnittlichen Buchpreis liegen.

> [!NOTE]
> Der XSLT-Debugger ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="start-debugging"></a>Starten des Debugvorgangs

1. Wählen Sie im Menü **Datei** die Option > **Datei** **Öffnen** aus.

2. Suchen Sie die Datei *below-average. xsl* , und wählen Sie **Öffnen**aus.

   Das Stylesheet wird im XML-Editor geöffnet.

3. Klicken Sie im Dokumenteigenschaften Fenster im Feld **Eingabe** auf die Schaltfläche zum Durchsuchen ( **...** ). (Wenn das **Eigenschaften** Fenster nicht sichtbar ist, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in der geöffneten Datei im Editor, und wählen Sie dann **Eigenschaften**aus.)

4. Suchen Sie die Datei *Books. XML* , und wählen Sie dann **Öffnen**aus.

   Dadurch wird die Quelldokument Datei festgelegt, die für die XSLT-Transformation verwendet wird.

5. Legen Sie einen [Breakpoint](../debugger/using-breakpoints.md) in Zeile 12 von *below-average. xsl*fest. Hierfür gibt es mehrere Möglichkeiten:

   - Klicken Sie in Zeile 12 auf den Rand des Editors.

   - Klicken Sie in Zeile 12 auf eine beliebige Stelle, und drücken Sie **F9**.

   - Klicken Sie mit der rechten Maustaste auf das `xsl:if` Starttag, und wählen Sie dann halte **Punkt** > halte **Punkt einfügen**aus.

      ![Haltepunkt in XSL-Datei in Visual Studio einfügen](media/insert-breakpoint.PNG)

6. Wählen Sie in der Menüleiste die Option **XML** > **XSLT-Debuggen starten** aus (oder drücken Sie **alt**+**F5**).

   Der Debugprozess wird gestartet.

   Im Editor befindet sich der Debugger auf dem `xsl:if`-Element des Stylesheets. Eine andere Datei mit dem Namen *below-average. XML* wird im Editor geöffnet. Dies ist die Ausgabedatei, die ausgefüllt wird, wenn jeder Knoten in der Eingabedatei *Books. XML* verarbeitet wird.

   Die Fenster **Auto, lokal und über** **Wachen 1** **werden unten**im Visual Studio-Fenster angezeigt. Im **Fenster Lokal** werden alle lokalen Variablen und ihre aktuellen Werte angezeigt. Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.

## <a name="watch-window"></a>Überwachungsfenster

Wir fügen dem Fenster "über **Wachen 1** " zwei Variablen hinzu, damit wir Ihre Werte untersuchen können, wenn die Eingabedatei verarbeitet wird. (Sie können auch das Fenster "lokal" verwenden, um Werte zu überprüfen, **Wenn die zu** überwachenden Variablen bereits vorhanden sind.)

1. Wählen Sie im Menü **Debuggen** die Option **Windows** > **Überwachung** > **ansehen 1**aus.

   Das Fenster über **Wachen 1** wird sichtbar.

2. Geben Sie `$bookAverage` in das Feld **Name** ein, und drücken Sie dann die **Eingabe**Taste.

   Der Wert der `$bookAverage`-Variablen wird im Feld **Wert** angezeigt.

3. Geben Sie in der nächsten Zeile `self::node()` in das Feld **Name** ein, und drücken **Sie**dann die EINGABETASTE.

   `self::node()` ist ein XPath-Ausdruck, der den aktuellen Kontext Knoten ergibt. Der Wert des `self::node()`-XPath-Ausdrucks ist der erste {2}book{3}-Knoten. Dieser ändert sich im Laufe der Transformation.

4. Erweitern Sie den Knoten `self::node()`, und erweitern Sie dann den Knoten, der den Wert `price`hat.

   ![Überwachungsfenster während des XSLT-Debuggens in Visual Studio](media/xslt-debugging-watch-window.png)

   Sie können den Wert des Buchpreises für den aktuellen Buch Knoten anzeigen und ihn mit dem `$bookAverage` Wert vergleichen. Da der Buchpreis unter dem Durchschnitt liegt, sollte die `xsl:if` Bedingung erfolgreich sein, wenn Sie den Debugvorgang fortsetzen.

## <a name="step-through-the-code"></a>Schrittweises Durchlaufen des Codes

1. Drücken Sie **F5**, um fortzufahren.

   Da der erste Buch Knoten die `xsl:if` Bedingung erfüllt, wird der Buch Knoten der Ausgabedatei " *below-average. XML* " hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich nun auf dem zweiten book-Knoten in der Datei *Books. XML* .

   Im Fenster über **Wachen 1** ändert sich der Wert `self::node()` in den zweiten Buch Knoten. Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`-Bedingung fehlschlägt.

2. Drücken Sie **F5**, um fortzufahren.

   Da der zweite Buch Knoten die `xsl:if` Bedingung nicht erfüllt, wird der book-Knoten nicht zur *below-average. XML* -Ausgabedatei hinzugefügt. Der Debugger wird weiter ausgeführt, bis er erneut auf dem `xsl:if`-Element im Stylesheet positioniert ist. Der Debugger befindet sich nun auf dem dritten `book` Knoten in der Datei *Books. XML* .

   Im Fenster über **Wachen 1** wird der `self::node()` Wert in den dritten Buch Knoten geändert. Durch Untersuchen des Werts des `price` Elements können Sie feststellen, dass der Preis unter dem Durchschnitt liegt. Die `xsl:if` Bedingung sollte erfolgreich sein.

3. Drücken Sie **F5**, um fortzufahren.

   Da die `xsl:if` Bedingung erfüllt wurde, wird das dritte Buch der Ausgabedatei " *below-average. XML* " hinzugefügt. Alle Bücher im XML-Dokument wurden verarbeitet, und der Debugger wird beendet.

## <a name="sample-files"></a>Beispieldateien

Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.

### <a name="below-averagexsl"></a>below-average. Xsl

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
