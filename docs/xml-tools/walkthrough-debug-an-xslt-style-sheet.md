---
title: 'Exemplarische Vorgehensweise: Debuggen von XSLT-Stylesheets | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 21018eb6e1a3ff282a7ec9fb856c431f894dafca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets
Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT-Debuggers veranschaulicht. Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes. Das Stylesheet sucht alle Bücher, deren Preis unter dem durchschnittlichen Buchpreis liegt.  
  
### <a name="to-prepare-for-this-walkthrough"></a>So bereiten Sie diese exemplarische Vorgehensweise vor  
  
1.  Schließen Sie alle geöffneten Projektmappen.  
  
2.  Kopieren Sie die zwei Beispieldateien auf den lokalen Computer.  
  
## <a name="start-debugging"></a>Starten des Debuggens  
  
#### <a name="to-start-debugging"></a>So starten Sie das Debuggen  
  
1.  Aus der **Datei** Sie im Menü **öffnen**, und klicken Sie auf **Datei**.  
  
2.  Suchen Sie die Datei belowAvg.xsl, und klicken Sie auf **öffnen**.  
  
     Im XML-Editor wird das Stylesheet geöffnet.  
  
3.  Klicken Sie auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Eingabe** Feld Eigenschaftenfenster des Dokuments.  
  
4.  Suchen Sie nach der Datei books.xml, und klicken Sie auf **öffnen**.  
  
     Damit legen Sie die Quelldokumentdatei fest, die für die XSLT-Transformation verwendet wird.  
  
5.  Mit der rechten Maustaste die `xsl:if` Starttag, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.  
  
6.  Klicken Sie auf die **XSLT Debuggen** Schaltfläche auf der Symbolleiste des XML-Editors.  
  
Hiermit wird der Debug-Vorgang gestartet, und es werden mehrere neue Fenster geöffnet, die vom Debugger verwendet werden.  
  
In zwei Fenstern werden Eingabedokument und Stylesheet angezeigt. Der Debugger zeigt in diesen Fenstern den aktuellen Ausführungszustand an. Der Debugger ist im `xsl:if`-Element des Stylesheets und im ersten book-Knoten der Datei books.xml positioniert.  
  
Im Lokalfenster werden alle lokalen Variablen mit ihren aktuellen Werten angezeigt. Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.  
  
Die **XSL-Ausgabe** Fenster zeigt die Ausgabe der XSL-Transformation. Dieses Fenster ist unabhängig von der **Ausgabefenster von Visual Studio** Fenster.  
  
## <a name="watch-window"></a>Überwachungsfenster  
  
#### <a name="to-use-the-watch-window"></a>So verwenden Sie das Überwachungsfenster  
  
1.  Aus der **Debuggen** Sie im Menü **Windows**, zeigen Sie auf **Überwachen**, und klicken Sie auf **Überwachen 1**.  
  
     Dadurch wird das Fenster Überwachen 1 aufgerufen.  
  
2.  Typ `$bookAverage` in der **Namen** Feld, und drücken Sie die EINGABETASTE.  
  
     Der Wert der `$bookAverage`-Variablen wird im Fenster angezeigt.  
  
3.  Typ `self::node()` in der **Namen** Feld, und drücken Sie die EINGABETASTE.  
  
     `self::node()` ist ein XPath-Ausdruck, der den aktuellen Kontextknoten auswertet. Der Wert des `self::node()`-XPath-Ausdrucks ist der erste book-Knoten. Dieser ändert sich im Laufe der Transformation.  
  
4.  Erweitern Sie den `self::node()`-Knoten, und erweitern Sie dann den `price`-Knoten.  
  
     Dadurch können Sie den Wert des Buchpreises sehen und ihn leicht mit dem `$bookAverage`-Wert vergleichen. Da der Buchpreis weniger als der Durchschnitt beträgt, muss die `xsl:if`-Bedingung erfolgreich sein.  
  
## <a name="step-through-the-code"></a>Schrittweises Ausführen des Codes  
 Mithilfe des Debuggers können Sie den Code zeilenweise ausführen.  
  
#### <a name="to-step-through-the-code"></a>So führen Sie den Code schrittweise aus  
  
1.  Drücken Sie **F5** um den Vorgang fortzusetzen.  
  
     Da der erste book`xsl:if`-Knoten die -Bedingung erfüllt, wird der book-Knoten dem XSL-Ausgabefenster hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich jetzt am zweiten book-Knoten in der Datei books.xml.  
  
     Im Fenster Überwachen 1`self::node()` wird der -Wert auf den zweiten book-Knoten geändert. Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`-Bedingung fehlschlägt.  
  
2.  Drücken Sie **F5** um den Vorgang fortzusetzen.  
  
     Da der zweite book`xsl:if`-Knoten die -Bedingung nicht erfüllt, wird er nicht im XSL-Ausgabefenster hinzugefügt. Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`-Element im Stylesheet befindet. Der Debugger befindet sich jetzt am dritten `book`-Knoten in der Datei books.xml.  
  
     Im Fenster Überwachen 1`self::node()` wird der -Wert auf den dritten book-Knoten geändert. Durch Auswertung des Werts für das `price`-Element können Sie ermitteln, dass der Preis unter dem Durchschnitt liegt und damit die `xsl:if`-Bedingung erfüllt ist.  
  
3.  Drücken Sie **F5** um den Vorgang fortzusetzen.  
  
     Da die `xsl:if`-Bedingung erfüllt war, wurde das dritte Buch dem XSL-Ausgabefenster hinzugefügt. Alle Bücher im XML-Dokument wurden verarbeitet, und der Debugger wird beendet.  
  
## <a name="sample-files"></a>Beispieldateien  
 Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.  
  
### <a name="belowavgxsl"></a>belowAvg.xsl  
  
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
        <xsl:if test="price < $bookAverage">  
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
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)