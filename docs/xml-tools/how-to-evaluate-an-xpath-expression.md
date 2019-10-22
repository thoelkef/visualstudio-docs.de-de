---
title: Auswerten eines XPath-Ausdrucks beim Debuggen
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 523c89af70c762f0cd0e31519c8c862c440c79eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654271"
---
# <a name="evaluate-xpath-expressions"></a>XPath-Ausdrücke auswerten

Sie können XPath-Ausdrücke auswerten, indem Sie das Fenster **schnell Überwachung** während des Debuggens verwenden. Der XPath-Ausdruck muss gemäß der W3C-Empfehlung für XPath 1.0 gültig sein. Der aktuelle XSLT-Kontext (d. h. der `self::node()` Knoten **im Fenster Lokal** ) stellt den Auswertungs Kontext für den XPath-Ausdruck bereit.

Beim Auswerten eines XPath-Ausdrucks:

- Integrierte XPath-Funktionen werden unterstützt.

- Integrierte XSLT-Funktionen und benutzerdefinierte Funktionen werden nicht unterstützt.

> [!NOTE]
> Das XSLT-Debuggen ist nur in der Enterprise Edition von Visual Studio verfügbar.

## <a name="evaluate-an-xpath-expression"></a>Auswerten eines XPath-Ausdrucks

Im folgenden Verfahren werden die Dateien *below-average. xsl* und *Books. XML* aus der Seite Exemplarische Vorgehens [Weise: Debuggen eines XSLT-Stylesheets](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) verwendet.

1. Fügen Sie einen Haltepunkt am `xsl:if`-Starttag ein.

2. Um das Debuggen zu starten, wählen Sie in der Menüleiste die Optionen **XML**  > **XSLT-Debugging starten** aus (oder drücken Sie **alt** +**F5**).

   Der Debugger wird gestartet und am `xsl:if`-Tag unterbrochen.

3. Klicken Sie mit der rechten Maustaste auf **schnell Überwachung**.

   Das Fenster **schnell Überwachung** wird geöffnet.

4. Geben Sie im Dialogfeld **schnell Überwachung** `./price/text()` in das Feld **Ausdruck** ein, und wählen Sie dann **neu auswerten**aus.

   Der Preis für den aktuellen Buch Knoten wird im Feld **Wert** angezeigt.

   ![Auswerten eines XPath-Ausdrucks im Fenster "schnell Überwachung"](media/quickwatch-price.png)

5. Ändern Sie den XPath-Ausdruck in `./price/text() < $bookAverage` und klicken Sie dann auf **neu auswerten**.

   Im Feld **Wert** wird angezeigt, dass der XPath-Ausdruck zu `true` ausgewertet wird.

## <a name="see-also"></a>Siehe auch

- [Debuggen von XSLT](../xml-tools/debugging-xslt.md)