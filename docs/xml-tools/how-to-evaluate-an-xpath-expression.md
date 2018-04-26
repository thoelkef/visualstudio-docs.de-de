---
title: 'Gewusst wie: Auswerten eines XPath-Ausdrucks'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2956e0c19e7cf50fdde39765bc5b26112986b84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Gewusst wie: Auswerten eines XPath-Ausdrucks

Sie können XPath-Ausdrücken mit Auswerten der **Schnellüberwachung** (Dialogfeld). Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext – d. h. die `self::node()` Knoten in der **"lokal"** Fenster – stellt den Auswertungskontext für den XPath-Ausdruck bereit.

 In der folgenden Liste wird beschrieben, welche Funktionen beim Auswerten eines XPath-Ausdrucks unterstützt werden:

-   Integrierte XPath-Funktionen werden unterstützt.

-   Integrierte XSLT-Funktionen werden nicht unterstützt.

-   Benutzerdefinierte Funktionen werden nicht unterstützt.

> [!NOTE]
> Im folgenden Verfahren wird die belowAvg.xsl und books.xml Dateien aus dem [Exemplarische Vorgehensweise: Debuggen von XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) Thema.

## <a name="to-evaluate-an-xpath-expression"></a>So werten Sie einen XPath-Ausdruck aus

1.  Fügen Sie einen Haltepunkt am `xsl:if`-Starttag ein.

2.  Klicken Sie auf die **XSLT Debuggen** Schaltfläche auf der Symbolleiste des XML-Editors.

     Der Debugger wird gestartet und am `xsl:if`-Tag unterbrochen.

3.  Mit der rechten Maustaste, und wählen Sie **Schnellüberwachung**.

     Die **Schnellüberwachung** Dialogfeld wird angezeigt.

4.  Geben Sie `./price/text()` in der **Ausdruck** Feld der **Schnellüberwachung** (Dialogfeld), und klicken Sie auf **neu auswerten**.

     Der Preis des aktuellen Knotens Buch wird angezeigt, der **Wert** Feld.

5.  Ändern Sie die XPath-Ausdruck zur `./price/text() < $bookAverage` , und klicken Sie auf **neu auswerten**.

     Die **Wert** Feld zeigt, dass der XPath-Ausdruck ergibt `true`.

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)