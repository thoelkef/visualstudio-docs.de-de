---
title: "Gewusst wie: Auswerten eines XPath-Ausdrucks | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Gewusst wie: Auswerten eines XPath-Ausdrucks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können XPath\-Ausdrücke mit dem Dialogfeld **Schnellüberwachung** auswerten.Der XPath\-Ausdruck muss gemäß der W3C\-Empfehlung für XPath 1.0 gültig sein.Der aktuelle XSLT\-Kontext, d. h. der `self::node()`\-Knoten im **Lokalfenster**, stellt den Auswertungskontext für den XPath\-Ausdruck bereit.  
  
 In der folgenden Liste wird beschrieben, welche Funktionen beim Auswerten eines XPath\-Ausdrucks unterstützt werden:  
  
-   Integrierte XPath\-Funktionen werden unterstützt.  
  
-   Integrierte XSLT\-Funktionen werden nicht unterstützt.  
  
-   Benutzerdefinierte Funktionen werden nicht unterstützt.  
  
> [!NOTE]
>  In der folgenden Prozedur werden die Dateien **belowAvg.xsl** und **books.xml** aus dem Thema [Exemplarische Vorgehensweise: Debuggen eines XSLT\-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) verwendet.  
  
### So werten Sie einen XPath\-Ausdruck aus  
  
1.  Fügen Sie einen Haltepunkt am `xsl:if`\-Starttag ein.  
  
2.  Klicken Sie auf der Symbolleiste des XML\-Editors auf die Schaltfläche **XSL debuggen**.  
  
     Der Debugger wird gestartet und am `xsl:if`\-Tag unterbrochen.  
  
3.  Klicken Sie mit der rechten Maustaste, und wählen Sie die Option **Schnellüberwachung** aus.  
  
     Das Dialogfeld **Schnellüberwachung** wird angezeigt.  
  
4.  Geben Sie im Dialogfeld **Schnellüberwachung** im Feld **Ausdruck** den Ausdruck `./price/text()` ein, und klicken Sie auf **Neu auswerten**.  
  
     Der Preis des aktuellen **book**\-Knotens wird im Feld **Wert** angezeigt.  
  
5.  Ändern Sie den XPath\-Ausdruck in `./price/text() < $bookAverage`, und klicken Sie auf **Neu auswerten**.  
  
     Im Feld **Wert** wird angezeigt, dass der XPath\-Ausdruck als `true` ausgewertet wird.  
  
## Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)