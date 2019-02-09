---
title: 'Vorgehensweise: Auswerten eines XPath-Ausdrucks'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b43a82d476e4426b1428f072cc980dbc8631cff2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970399"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Vorgehensweise: Auswerten eines XPath-Ausdrucks

Sie können die XPath-Ausdrücken mit Auswerten der **Schnellüberwachung** Dialogfeld. Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext – d. h. die `self::node()` Knoten in der **"lokal"** Fenster – stellt den Auswertungskontext für den XPath-Ausdruck.

 In der folgenden Liste wird beschrieben, welche Funktionen beim Auswerten eines XPath-Ausdrucks unterstützt werden:

-   Integrierte XPath-Funktionen werden unterstützt.

-   Integrierte XSLT-Funktionen werden nicht unterstützt.

-   Benutzerdefinierte Funktionen werden nicht unterstützt.

> [!NOTE]
> Im folgenden Verfahren wird die *belowAvg.xsl* und *books.xml* Dateien aus dem [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) Thema.

## <a name="to-evaluate-an-xpath-expression"></a>So werten Sie einen XPath-Ausdruck aus

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

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)