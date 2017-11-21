---
title: 'Exemplarische Vorgehensweise: Verwenden von XSLT-Hierarchie | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e60c8ec-cd05-4597-b856-55038218acf4
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b0cd7d0567f12a7f1d57bdea765cbf9eb555dd8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Exemplarische Vorgehensweise: Verwenden der XSLT-Hierarchie
Das XSLT-Hierarchietool vereinfacht viele XML-Entwicklungsaufgaben. In einem XSLT-Stylesheet werden oft `includes`- und `imports`-Anweisungen verwendet. Die Kompilierung beginnt mit dem Hauptstylesheet. Wenn in Folge der Kompilierung eines XSLT-Stylesheets ein Fehler angezeigt wird, kann dieser jedoch aus einer anderen Quelle als dem Hauptstylesheet stammen. Zum Beheben des Fehlers oder Bearbeiten des Stylesheets müssen Sie möglicherweise auf eingeschlossene oder importierte Stylesheets zugreifen. Beim schrittweisen Ausführen des Stylesheets im Debugger werden ggf. eingeschlossene und importierte Stylesheets geöffnet, und Sie können einen Haltepunkt in den eingeschlossenen Stylesheets hinzufügen.  
  
 Ein anderes Szenario, in dem das XSLT-Hierarchietool nützlich sein kann, ist das Einfügen von Haltepunkten in den integrierten Vorlagenregeln. Vorlagenregeln sind spezielle, für jeden Modus des Stylesheets generierte Vorlagen, die von `xsl:apply-templates` aufgerufen werden, wenn keine andere Vorlage dem Knoten entspricht. Der XSLT-Debugger generiert die Datei mit den Regeln im temporären Ordner und kompiliert sie zusammen mit dem Hauptstylesheet, um das Debugging in integrierten Vorlagenregeln zu implementieren. Ohne einen Einzelschritt von `xsl:apply-template` in den Code kann es schwierig sein, im Hauptstylesheet enthaltene Stylesheets zu finden oder das Stylesheet mit den integrierten Vorlagenregeln zu finden und zu öffnen.  
  
 Im Beispiel in diesem Thema wird das Debugging in einem referenzierten Stylesheet veranschaulicht.  
  
### <a name="procedure-title"></a>Titel des Verfahrens  
  
1.  Öffnen Sie in Visual Studio ein XML-Dokument. In diesem Beispiel wird das folgende Dokument `collection.xml` verwendet.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>  
    <COLLECTION>  
      <BOOK>  
        <TITLE>Lover Birds</TITLE>  
        <AUTHOR>Cynthia Randall</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>The Sundered Grail</TITLE>  
        <AUTHOR>Eva Corets</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>Splish Splash</TITLE>  
        <AUTHOR>Paula Thurman</AUTHOR>  
        <PUBLISHER>Scootney</PUBLISHER>  
      </BOOK>  
    </COLLECTION>  
    ```  
  
2.  Fügen Sie die folgende Datei `xslincludefile.xsl` hinzu:  
  
    ```  
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
          xml:space="preserve">  
  
    <xsl:template match="TITLE">  
       Title - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="AUTHOR">  
       Author - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="PUBLISHER">  
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->  
    </xsl:template>  
  
    </xsl:stylesheet>  
    ```  
  
3.  Fügen Sie die folgende Datei `xslinclude.xsl` hinzu:  
  
    ```  
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  
      <xsl:output method="xml" omit-xml-declaration="yes"/>  
  
      <xsl:template match="/">  
        <xsl:for-each select="COLLECTION/BOOK">  
          <xsl:apply-templates select="TITLE"/>  
          <xsl:apply-templates select="AUTHOR"/>  
          <xsl:apply-templates select="PUBLISHER"/>  
          <BR/>  
          <!-- add this -->  
        </xsl:for-each>  
      </xsl:template>  
  
      <!-- The following template rule will not be called,  
      because the related template in the including stylesheet  
      is called. If we move this template so that  
      it follows the xsl:include instruction, this one  
      will be called instead.-->  
      <xsl:template match="TITLE">  
        <DIV STYLE="color:blue">  
          Title: <xsl:value-of select="."/>  
        </DIV>  
      </xsl:template>  
  
      <xsl:include href="xslincludefile.xsl" />  
    </xsl:stylesheet>  
    ```  
  
4.  Fügen Sie einen Haltepunkt bei der Anweisung hinzu: `<xsl:include href="xslincludefile.xsl" />`  
  
5.  Beginnen Sie mit dem Debuggen.  
  
6.  Klicken Sie auf die Schaltfläche "Einzelschritt", wenn der Debugger bei der `<xsl:include href="xslincludefile.xsl" />`-Anweisung anhält. Das Debugging kann im referenzierten Stylesheet fortgesetzt werden. Die Hierarchie ist sichtbar, und im Designer wird der richtige Pfad angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: XSLT-Profiler](../xml-tools/walkthrough-xslt-profiler.md)