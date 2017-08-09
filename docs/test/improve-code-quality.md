---
title: "Verbessern der Codequalität"
ms.custom: na
ms.date: 02/17/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: db500747061b436db2a0897e5b43a1cae4a3acae
ms.contentlocale: de-de
ms.lasthandoff: 06/03/2017

---
# <a name="improve-code-quality"></a>Verbessern der Codequalität
Was ist Codequalität? Korrektheit, Wartbarkeit und sogar Eleganz spielen beim Erstellen von gutem Code eine Rolle. Unabhängig davon, wie Sie Codequalität definieren, können die Visual Studio-Testtools Sie und Ihr Team dabei unterstützen, einen hohen Standard für hervorragenden Code einzuhalten.  
  
 **Anforderungen**  
  
-   Einige der Tools und Funktionen, die in diesem Abschnitt beschrieben werden, sind nur in bestimmten Editionen von Visual Studio verfügbar – sie sind nicht generell in Visual Studio verfügbar. In der Dokumentation für diese Tools und Funktionen werden die bestimmten Editionsanforderungen aufgeführt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In der folgenden Tabelle finden Sie die Beschreibungen häufiger Aufgaben und Links zu weiteren Informationen zur erfolgreichen Ausführung dieser Aufgaben.  
  
|||  
|-|-|  
|[Komponententest für Code](../test/unit-test-your-code.md)|Test-Explorer vereinfacht die Integration von Komponententests in die Entwicklungspraxis. Sie können entweder das Microsoft-Komponententest-Framework oder ein Drittanbieter- oder Open-Source-Framework verwenden.|  
|[Live Unit Testing mit Visual Studio 2017](../test/live-unit-testing.md)|Live Unit Testing führt automatisch Komponententests im Hintergrund aus und stellt Codeabdeckung und Testergebnisse im Code-Editor von Visual Studio grafisch dar.|  
|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|Analysetools für statischen Code finden Entwurfs-, Nutzungs-, Wartbarkeits- und Formatprobleme in C++ und verwaltetem Code. Viele dieser Probleme können zu Fehlern führen, die in der Standardtestumgebung nur schwer zu reproduzieren sind.|  
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Die Metrik umfasst einen Wartbarkeitsindex für Funktionen und Klassen, die zyklomatische Komplexität von Funktionen, die Vererbungstiefe von Klassen und die Anzahl der Kopplungen von Klassen.|  
  
## <a name="related-scenarios"></a>Ähnliche Szenarien  
 [DevOps-Übersicht für Team Services und TFS](https://www.visualstudio.com/docs/devops-alm-overview)  
 Wenn Sie mit Visual Studio Team Foundation und Visual Studio Team Services nicht vertraut sind, erfahren Sie mehr zu deren Verwendung in einer Teamentwicklungsumgebung, um die Produktivität zu steigern und Risiken zu minimieren, die mit der Anwendungsentwicklung einhergehen.  
  
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)  
 Sie können [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] verwenden, um die Herausforderungen und die Komplexität der Softwareentwicklung zu verwalten. Mit [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] können Sie die Anwendung visuell modellieren, sowohl im aktuellen Zustand als auch im gewünschten, künftigen Zustand. Sie können Diagramme erstellen und verwalten, die Ihnen bei der Visualisierung der logischen Modelle der Anwendung helfen und gleichzeitig eine Zuordnung zu den physischen Modellen herstellen. Dadurch sind Sie in der Lage, die im Entwurf befindliche Software zu ändern, zu überprüfen und zu analysieren.  
  
 [Testen der Anwendung](https://www.visualstudio.com/docs/test/overview)  
 Verwenden Sie [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)], um Ihre Produktivität für den gesamten Testlebenszyklus zu steigern. Mit [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] oder [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] planen Sie den Testaufwand. Sie können sowohl manuelle als auch automatisierte Tests erstellen, verwalten, bearbeiten und ausführen. Außerdem können Sie den Testfortschritt anhand Ihres Plans überprüfen.  
  
 [Schützen der Anwendung mit PreEmptive Protection – Dotfuscator](../ide/dotfuscator/index.md)  
 Verwenden Sie die kostenlose Dotfuscator Community Edition (CE), um Geschäftsgeheimnisse und sonstiges geistiges Eigentum zu sichern, Piraterie und Fälschungen zu reduzieren und Schutz vor Manipulationen und nicht autorisiertem Debuggen zu bieten.  Dotfuscator schützt und sichert kompilierte Assemblys ohne zusätzliche Programmierung und sogar ohne Zugriff auf den Quellcode.
  
 [Erstellen der Anwendung](https://www.visualstudio.com/docs/build/overview)  
 Sie können [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] verwenden, um automatisierte Builds für den Code zu erstellen und zu verwalten. [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] ermöglicht das Erstellen von Ablageservern zum Bereitstellen von Builds. Außerdem können Sie Buildtrends analysieren.  
  
 [Nachverfolgen von Arbeit mit Visual Studio Online oder Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 Mithilfe von [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] können Sie Projekte planen und nachverfolgen, unabhängig davon, ob Sie den agilen Prozess, den formalen Prozess oder eine Variation dieser Prozesse verwenden. Indem Sie Ihre Projekte planen, den Status im Hinblick auf den Plan nachverfolgen und notwendige Anpassungen vornehmen, können Sie Risiken minimieren, unerfreuliche Überraschungen vermeiden und die Kosten der Projekte verwalten.

