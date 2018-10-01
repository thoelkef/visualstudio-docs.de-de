---
title: 'Vorgehensweise: Auswerten eines XPath-Ausdrucks | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 82d1330860a67b5dcb2ea52777bd84cceda4db00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522238"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Gewusst wie: Auswerten eines XPath-Ausdrucks
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die XPath-Ausdrücken mit Auswerten der **Schnellüberwachung** Dialogfeld. Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext – d. h. die `self::node()` Knoten in der **"lokal"** Fenster – stellt den Auswertungskontext für den XPath-Ausdruck.  
  
 In der folgenden Liste wird beschrieben, welche Funktionen beim Auswerten eines XPath-Ausdrucks unterstützt werden:  
  
-   Integrierte XPath-Funktionen werden unterstützt.  
  
-   Integrierte XSLT-Funktionen werden nicht unterstützt.  
  
-   Benutzerdefinierte Funktionen werden nicht unterstützt.  
  
> [!NOTE]
>  Im folgenden Verfahren wird die belowAvg.xsl und books.xml Dateien aus dem [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) Thema.  
  
### <a name="to-evaluate-an-xpath-expression"></a>So werten Sie einen XPath-Ausdruck aus  
  
1.  Fügen Sie einen Haltepunkt am `xsl:if`-Starttag ein.  
  
2.  Klicken Sie auf die **XSLT Debuggen** auf der Symbolleiste des XML-Editor.  
  
     Der Debugger wird gestartet und am `xsl:if`-Tag unterbrochen.  
  
3.  Mit der rechten Maustaste, und wählen Sie **Schnellüberwachung**.  
  
     Die **Schnellüberwachung** Dialogfeld wird angezeigt.  
  
4.  Geben Sie `./price/text()` in die **Ausdruck** Feld der **Schnellüberwachung** Dialogfeld und klicken Sie auf **neu auswerten**.  
  
     Der Preis für den aktuellen Buchknoten angezeigt wird, der **Wert** Feld.  
  
5.  Ändern Sie die XPath-Ausdruck zur `./price/text() < $bookAverage` , und klicken Sie auf **neu auswerten**.  
  
     Die **Wert** Feld zeigt, dass der XPath-Ausdruck ergibt `true`.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)

