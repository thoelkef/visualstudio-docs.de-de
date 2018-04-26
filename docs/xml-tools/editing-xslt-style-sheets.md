---
title: Bearbeiten von XSLT-Stylesheets
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16a7d850f8045ce70166bec3324470abaf61b6de
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="editing-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets

Mit dem XML-Editor können auch XSLT-Stylesheets bearbeitet werden. Sie können die Vorteile der Standardfeatures des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Features, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Features
 In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Funktionen beschrieben.

 **Syntaxfarben**

 XSLT-Schlüsselwörter, wie z. B. `template`, `match`usw., werden angezeigt, in der XSLT-Schlüsselwort Farbe gemäß der **Schriftarten und Farben** Einstellungen.

 **Wellenförmige unterstreichungen**

 Der XML-Editor validiert mithilfe der installierten XSLT.XSD-Datei die XSLT-Stylesheets. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder -warnungen mit entsprechenden wellenförmigen Unterstreichungen.

 **Unterstützung von Skriptblöcken**

 Code in Skriptblöcken wird vom XSLT-Debugger unterstützt. Daher können Sie Haltepunkte festlegen und den Skriptblockcode schrittweise ausführen.

 **Die XSLT-Ausgabe anzeigen**

 Sie können eine XSL-Transformation ausführen und die Ausgabe im XML-Editor anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen einer XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Debuggen von XSLT**

 Sie können den XSLT-Debugger aus einer XSLT-Datei im XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [XSLT Debuggen](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)