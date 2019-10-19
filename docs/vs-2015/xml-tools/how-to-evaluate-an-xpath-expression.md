---
title: 'Gewusst wie: Auswerten eines XPath-Ausdrucks | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670866"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Gewusst wie: Auswerten eines XPath-Ausdrucks
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können XPath-Ausdrücke mit dem Dialogfeld **schnell Überwachung** auswerten. Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext – d. h. der `self::node()` Knoten **im Fenster Lokal** – stellt den Auswertungs Kontext für den XPath-Ausdruck bereit.

 In der folgenden Liste wird beschrieben, welche Funktionen beim Auswerten eines XPath-Ausdrucks unterstützt werden:

- Integrierte XPath-Funktionen werden unterstützt.

- Integrierte XSLT-Funktionen werden nicht unterstützt.

- Benutzerdefinierte Funktionen werden nicht unterstützt.

> [!NOTE]
> Im folgenden Verfahren werden die Dateien "belowAvg. xsl" und "Books. xml" aus dem Thema Exemplarische Vorgehens [Weise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) verwendet.

### <a name="to-evaluate-an-xpath-expression"></a>So werten Sie einen XPath-Ausdruck aus

1. Fügen Sie einen Haltepunkt am `xsl:if`-Starttag ein.

2. Klicken Sie im XML-Editor auf die Schaltfläche **XSL debuggen** .

     Der Debugger wird gestartet und am `xsl:if`-Tag unterbrochen.

3. Klicken Sie mit der rechten Maustaste auf **schnell Überwachung**.

     Das Dialogfeld **schnell Überwachung** wird angezeigt.

4. Geben Sie im Dialogfeld **schnell Überwachung** `./price/text()` in das Feld **Ausdruck** ein, und klicken Sie auf **neu auswerten**.

     Der Preis für den aktuellen Buch Knoten wird im Feld **Wert** angezeigt.

5. Ändern Sie den XPath-Ausdruck in `./price/text() < $bookAverage` und klicken Sie dann auf **neu auswerten**.

     Im Feld **Wert** wird angezeigt, dass der XPath-Ausdruck zu `true` ausgewertet wird.

## <a name="see-also"></a>Siehe auch
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)
