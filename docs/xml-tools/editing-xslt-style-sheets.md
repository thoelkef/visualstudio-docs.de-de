---
title: Bearbeiten von XSLT-Stylesheets
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a8625defb0d9e8d656aac7bb3d2236d4f5bb9c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021883"
---
# <a name="edit-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets

Mit dem XML-Editor können auch XSLT-Stylesheets bearbeitet werden. Sie können die Vorteile der Standardfeatures des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Features, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Features
 In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Funktionen beschrieben.

 **Farben für Syntax**

 XSLT-Schlüsselwörter, wie z. B. `template`, `match`usw., werden angezeigt, in der XSLT-Schlüsselwort Farbe, die gemäß der **Schriftarten und Farben** Einstellungen.

 **Wellenförmige unterstreichungen**

 Der XML-Editor verwendet die installierte *xslt.xsd* Datei zum Überprüfen der XSLT-Stylesheets. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder -warnungen mit entsprechenden wellenförmigen Unterstreichungen.

 **Unterstützung von Skriptblöcken**

 Code in Skriptblöcken wird vom XSLT-Debugger unterstützt. Daher können Sie Haltepunkte festlegen und den Skriptblockcode schrittweise ausführen.

 **Anzeigen der XSLT-Ausgabe**

 Sie können eine XSL-Transformation ausführen und die Ausgabe im XML-Editor anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Ausführen eine XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Debug XSLT**

 Sie können den XSLT-Debugger aus einer XSLT-Datei im XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [XSLT Debuggen](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)