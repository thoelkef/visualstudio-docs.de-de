---
title: Bearbeiten von XSLT-Stylesheets | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670956"
---
# <a name="editing-xslt-style-sheets"></a>Bearbeiten von XSLT-Stylesheets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem XML-Editor können auch XSLT-Stylesheets bearbeitet werden. Sie können die Vorteile der Standardfunktionen des Editors nutzen, z. B. IntelliSense, Gliedern, XML-Ausschnitte usw. Außerdem gibt es auch neue Funktionen, die die Entwicklung in XSLT erleichtern.

## <a name="xslt-features"></a>XSLT-Funktionen
 In der folgenden Tabelle werden die für die Arbeit mit XSLT-Stylesheets spezifischen Features beschrieben.

 **Syntax Farbgebung** XSLT-Schlüsselwörter, wie z. b. `template` , `match` usw., werden in der XSLT-Schlüsselwort Farbe angezeigt, die in den Einstellungen für **Schriftarten und Farben** angegeben ist.

 **Wellenförmige Unterstreichungen** Der XML-Editor verwendet die installierte XSLT. xsd-Datei, um XSLT-Stylesheets zu validieren. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Der XML-Editor kompiliert auch das Stylesheet im Hintergrund und meldet Compilerfehler oder -warnungen mit entsprechenden wellenförmigen Unterstreichungen.

 **Unterstützung für Skriptblöcke** Code in Skript Blöcken wird vom XSLT-Debugger unterstützt, sodass Sie Haltepunkte festlegen und den Skriptblock Code schrittweise durchlaufen können.

 **XSLT-Ausgabe anzeigen** Sie können eine XSL-Transformation ausführen und die Ausgabe im XML-Editor anzeigen. Weitere Informationen finden Sie unter Gewusst [wie: Ausführen einer XSLT-Transformation im XML-Editor](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **XSLT Debuggen** Sie können den XSLT-Debugger über eine XSLT-Datei im XML-Editor starten. Der Debugger unterstützt das Festlegen von Haltepunkten in der XSLT-Datei, das Anzeigen des Ausführungszustands und weitere Vorgänge. Wenn auf eine XSLT-Variable gezeigt wird, wird eine QuickInfo mit dem Variablenwert angezeigt. Mit dem Debugger kann ein Stylesheet oder eine aus einer anderen Anwendung aufgerufene, kompilierte XSL-Transformation debuggt werden. Weitere Informationen finden Sie unter [Debuggen von XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Weitere Informationen
 [XML-Editor](../xml-tools/xml-editor.md)
