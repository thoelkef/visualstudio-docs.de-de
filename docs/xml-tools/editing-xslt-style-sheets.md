---
title: Bearbeiten von XSLT-Stylesheets
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dab4013bf3921a2af4f69d464c10d1e70f9407b3
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526203"
---
# <a name="edit-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets

Der XML-Editor kann auch verwendet werden, zum Bearbeiten von XSLT-Stylesheets. Sie können die Vorteile der Standardfunktionen des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Features, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Features

In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Features beschrieben.

**Farben für Syntax**

XSLT-Schlüsselwörter, wie z. B. `template` und `match`, werden angezeigt, in der XSLT-Schlüsselwort Farbe, die gemäß der **Schriftarten und Farben** Einstellungen.

**Wellenförmige unterstreichungen**

Der XML-Editor verwendet die installierte *xslt.xsd* Datei zum Überprüfen der XSLT-Stylesheets. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder Warnungen mit entsprechenden wellenförmigen unterstreichungen.

**Unterstützung von Skriptblöcken**

Code in Skriptblöcken wird vom XSLT-Debugger unterstützt. Daher können Sie Haltepunkte festlegen und den Skriptblockcode schrittweise ausführen.

**Anzeigen der XSLT-Ausgabe**

Sie können eine XSL-Transformation ausführen und zeigen Sie die Ausgabe der XML-Editor. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen eine XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Debug XSLT**

Sie können die XSLT-Debugger aus einer XSLT-Datei in der XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [XSLT Debuggen](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Siehe auch

- [XML-editor](../xml-tools/xml-editor.md)