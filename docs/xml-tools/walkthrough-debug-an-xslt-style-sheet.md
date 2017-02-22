---
title: "Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anhand der Schritte in dieser exemplarischen Vorgehensweise wird die Verwendung des XSLT\-Debuggers veranschaulicht.Zu den Schritten gehören das Anzeigen von Variablen, das Festlegen von Haltepunkten und das schrittweise Ausführen des Codes.Das Stylesheet sucht alle Bücher, deren Preis unter dem durchschnittlichen Buchpreis liegt.  
  
### So bereiten Sie die Ausführung der exemplarischen Vorgehensweise vor  
  
1.  Schließen Sie alle geöffneten Projektmappen.  
  
2.  Kopieren Sie die zwei Beispieldateien auf den lokalen Computer.  
  
## Starten des Debuggens  
  
#### So starten Sie das Debuggen  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, und klicken Sie auf **Datei**.  
  
2.  Markieren Sie die Datei **belowAvg.xsl**, und klicken Sie auf **Öffnen**.  
  
     Im XML\-Editor wird das Stylesheet geöffnet.  
  
3.  Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Eingabe** auf die Schaltfläche zum Durchsuchen \(**…**\).  
  
4.  Navigieren Sie zu der Datei **books.xml**, und klicken Sie auf **Öffnen**.  
  
     Damit wird die Quelldokumentdatei festgelegt, die für die XSLT\-Transformation verwendet wird.  
  
5.  Klicken Sie mit der rechten Maustaste auf das `xsl:if`\-Starttag, zeigen Sie auf **Haltepunkt**, und klicken Sie auf **Haltepunkt einfügen**.  
  
6.  Klicken Sie auf der Symbolleiste des XML\-Editors auf die Schaltfläche **XSL debuggen**.  
  
 Hiermit wird der Debug\-Vorgang gestartet, und es werden mehrere neue Fenster geöffnet, die vom Debugger verwendet werden.  
  
 In zwei Fenstern werden Eingabedokument und Stylesheet angezeigt.Der Debugger zeigt in diesen Fenstern den aktuellen Ausführungszustand an.Der Debugger ist im `xsl:if`\-Element des Stylesheets und im ersten **book**\-Knoten der Datei **books.xml** positioniert.  
  
 Im Lokalfenster werden alle lokalen Variablen mit ihren aktuellen Werten angezeigt.Das schließt die im Stylesheet definierten Variablen sowie Variablen ein, anhand derer der Debugger die Knoten verfolgt, die sich derzeit im Kontext befinden.  
  
 Im Fenster **XSL\-Ausgabe** wird die Ausgabe der XSL\-Transformation angezeigt.Dies ist ein anderes Fenster als das Ausgabefenster in Visual Studio.  
  
## Überwachungsfenster  
  
#### So verwenden Sie das Überwachungsfenster  
  
1.  Zeigen Sie im Menü **Debuggen** auf **Fenster**, zeigen Sie auf **Überwachen**, und klicken Sie auf **Überwachen 1**.  
  
     Dadurch wird das Fenster Überwachen 1 aufgerufen.  
  
2.  Geben Sie `$bookAverage` im Feld **Name** ein, und drücken Sie die EINGABETASTE.  
  
     Der Wert der `$bookAverage`\-Variablen wird im Fenster angezeigt.  
  
3.  Geben Sie `self::node()` im Feld **Name** ein, und drücken Sie die EINGABETASTE.  
  
     `self::node()` ist ein XPath\-Ausdruck, der den aktuellen Kontextknoten auswertet.Der Wert des `self::node()`\-XPath\-Ausdrucks ist der erste **book**\-Knoten.Dieser ändert sich im Laufe der Transformation.  
  
4.  Erweitern Sie den `self::node()`\-Knoten, und erweitern Sie dann den `price`\-Knoten.  
  
     Dadurch können Sie den Wert des Buchpreises sehen und ihn leicht mit dem `$bookAverage`\-Wert vergleichen.Da der Buchpreis weniger als der Durchschnitt beträgt, muss die `xsl:if`\-Bedingung erfolgreich sein.  
  
## Schrittweises Ausführen des Codes  
 Mithilfe des Debuggers können Sie den Code zeilenweise ausführen.  
  
#### So führen Sie den Code schrittweise aus  
  
1.  Zum Fortsetzen drücken Sie **F5**.  
  
     Da der erste **book**\-Knoten die `xsl:if`\-Bedingung erfüllt, wird der **book**\-Knoten dem XSL\-Ausgabefenster hinzugefügt.Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`\-Element im Stylesheet befindet.Der Debugger befindet sich jetzt am zweiten **book**\-Knoten in der Datei **books.xml**.  
  
     Im Fenster **Überwachen 1** wird der `self::node()`\-Wert auf den zweiten **book**\-Knoten geändert.Durch Auswertung des Werts für das Preiselement können Sie feststellen, dass der Preis über dem Durchschnitt liegt und folglich die `xsl:if`\-Bedingung fehlschlägt.  
  
2.  Zum Fortsetzen drücken Sie die Taste **F5**.  
  
     Da der zweite **book**\-Knoten die `xsl:if`\-Bedingung nicht erfüllt, wird er nicht im XSL\-Ausgabefenster hinzugefügt.Der Debugger setzt die Ausführung fort, bis er sich wieder am `xsl:if`\-Element im Stylesheet befindet.Der Debugger befindet sich jetzt am dritten `book`\-Knoten in der Datei **books.xml**.  
  
     Im Fenster **Überwachen 1** wird der `self::node()`\-Wert auf den dritten **book**\-Knoten geändert.Durch Auswertung des Werts für das `price`\-Element können Sie ermitteln, dass der Preis unter dem Durchschnitt liegt und damit die `xsl:if`\-Bedingung erfüllt ist.  
  
3.  Zum Fortsetzen drücken Sie die Taste **F5**.  
  
     Da die `xsl:if`\-Bedingung erfüllt war, wurde das dritte Buch dem XSL\-Ausgabefenster hinzugefügt.Alle Bücher im XML\-Dokument wurden verarbeitet, und der Debugger wird beendet.  
  
## Beispieldateien  
 Bei der exemplarischen Vorgehensweise werden die folgenden zwei Dateien verwendet.  
  
### belowAvg.xsl  
  
```  
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
  
### books.xml  
  
```  
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
  
## Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)