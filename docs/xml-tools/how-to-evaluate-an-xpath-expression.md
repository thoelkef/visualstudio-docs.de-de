---
title: Auswerten eines XPath-Ausdrucks während des Debuggens
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526321"
---
# <a name="evaluate-xpath-expressions"></a>Auswerten von XPath-Ausdrücken

Sie können die XPath-Ausdrücke auswerten, indem Sie mit der **Schnellüberwachung** Fenster während des Debuggens. Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext (d. h. die `self::node()` Knoten in der **"lokal"** Fenster) stellt den Auswertungskontext für den XPath-Ausdruck.

Wenn einen XPath-Ausdruck ausgewertet werden:

- Integrierte XPath-Funktionen werden unterstützt.

- Integrierte XSLT-Funktionen und benutzerdefinierte Funktionen werden nicht unterstützt.

> [!NOTE]
> XSLT-Debuggen ist nur verfügbar, in der Enterprise Edition von Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Wertet einen xpathausdruck

Im folgenden Verfahren wird die *unten average.xsl* und *books.xml* Dateien aus dem [Exemplarische Vorgehensweise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) Seite.

1. Fügen Sie einen Haltepunkt am `xsl:if`-Starttag ein.

2. Wählen Sie zum Starten des Debuggens **XML** > **XSLT Debuggen starten** in der Menüleiste (oder drücken Sie **Alt**+**F5** ).

   Der Debugger wird gestartet und am `xsl:if`-Tag unterbrochen.

3. Mit der rechten Maustaste, und wählen Sie **Schnellüberwachung**.

   Die **Schnellüberwachung** Fenster wird geöffnet.

4. Geben Sie `./price/text()` in die **Ausdruck** Feld der **Schnellüberwachung** Dialogfeld ein, und wählen Sie dann **neu auswerten**.

   Der Preis für den aktuellen Buchknoten angezeigt wird, der **Wert** Feld.

   ![Auswerten eines XPath-Ausdrucks, in dem Fenster Schnellüberwachung](media/quickwatch-price.png)

5. Ändern Sie die XPath-Ausdruck zur `./price/text() < $bookAverage` , und klicken Sie auf **neu auswerten**.

   Die **Wert** Feld zeigt, dass der XPath-Ausdruck ergibt `true`.

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)