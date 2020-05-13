---
title: Bearbeiten von XSLT-Stylesheets
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bab324c58c06cc1ca553bae2f81faf474c4ad0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592840"
---
# <a name="edit-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets

Mit dem XML-Editor können auch XSLT-Stylesheets bearbeitet werden. Sie können die Vorteile der Standardfunktionen des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Funktionen, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Funktionen

In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Features beschrieben.

**Farben für Syntax**

XSLT-Schlüsselwörter, z. B. `template` und `match`, werden in der Farbe für XSLT-Schlüsselwörter angezeigt, die in den Einstellungen **Schriftarten und Farben** angegeben ist.

**Wellenförmige Unterstreichungen**

Der XML-Editor validiert mithilfe der installierten *xslt.xsd*-Datei die XSLT-Stylesheets. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder -warnungen mit entsprechenden wellenförmigen Unterstreichungen.

**Unterstützung von Skriptblöcken**

Code in Skriptblöcken wird vom XSLT-Debugger unterstützt. Daher können Sie Haltepunkte festlegen und den Skriptblockcode schrittweise ausführen.

**Anzeige der XSLT-Ausgabe**

Sie können eine XSL-Transformation ausführen und die Ausgabe im XML-Editor anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen einer XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debuggen von XSLT**

Sie können den XSLT-Debugger aus einer XSLT-Datei im XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [Debuggen von XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
