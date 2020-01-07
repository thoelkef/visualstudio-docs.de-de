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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592840"
---
# <a name="edit-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets

Der XML-Editor kann auch zum Bearbeiten von XSLT-Stylesheets verwendet werden. Sie können die Vorteile der Standardfunktionen des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Funktionen, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Funktionen

In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Features beschrieben.

**Syntax Farbgebung**

XSLT-Schlüsselwörter wie `template` und `match`werden in der XSLT-Schlüsselwort Farbe angezeigt, die in den Einstellungen für **Schriftarten und Farben** angegeben ist.

**Wellenförmige Unterstreichungen**

Der XML-Editor verwendet die installierte *XSLT. xsd* -Datei, um XSLT-Stylesheets zu validieren. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder Warnungen mit entsprechenden wellenförmigen unterstrichen.

**Unterstützung für Skriptblöcke**

Code in Skriptblöcken wird vom XSLT-Debugger unterstützt. Daher können Sie Haltepunkte festlegen und den Skriptblockcode schrittweise ausführen.

**XSLT-Ausgabe anzeigen**

Sie können eine XSL-Transformation ausführen und die Ausgabe im XML-Editor anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen einer XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**XSLT Debuggen**

Sie können den XSLT-Debugger über eine XSLT-Datei im XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [Debuggen von XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
