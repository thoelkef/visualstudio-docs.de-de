---
title: "Verbessern der Codequalität"
ms.custom: na
ms.date: 10/14/2016
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
ms.author: mlearned
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
translationtype: Human Translation
ms.sourcegitcommit: 93f70de0acfa8b5efcfe141a1f8060061a4ba15d
ms.openlocfilehash: 0c439304b8a23166293fc4cc6d984947fd51f133
ms.lasthandoff: 02/22/2017

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
|[Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|Analysetools für statischen Code finden Entwurfs-, Nutzungs-, Wartbarkeits- und Formatprobleme in C++ und verwaltetem Code. Viele dieser Probleme können zu Fehlern führen, die in der Standardtestumgebung nur schwer zu reproduzieren sind.|  
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Bei der Codemetrik handelt es sich um eine Reihe von Softwaremaßstäben, die Entwicklern einen besseren Einblick in den von ihnen entwickelten Code bieten. Die Metrik umfasst einen Wartbarkeitsindex für Funktionen und Klassen, die zyklomatische Komplexität von Funktionen, die Vererbungstiefe von Klassen und die Anzahl der Kopplungen von Klassen.|  
|[PreEmptive Analytics für Team Foundation Server](http://msdn.microsoft.com/library/hh973124.aspx)|PreEmptive Analytics für TFS CE unterstützt Sie dabei, feedbackorientierte Entwicklungsprozesse in den Entwicklungsworkflow zu integrieren. Sobald Fehler während der Ausführung von Anwendungen auftreten, senden die Anwendungen automatisch Ausnahmeberichtdaten an Ihren PreEmptive Analytics-Dienst. Der Dienst erstellt dann auf Grundlage von selbst definierten Regeln und Schwellenwerten Arbeitselemente in Microsoft Team Foundation Server oder aktualisiert diese.|  
|[PreEmptive Dotfuscator und Analytics CE](assetId:///25d195d4-9f76-4dcc-9fbb-eeb9bdca9a3f)|PreEmptive Dotfuscator ist ein .NET-Verbergungs- und Komprimierungsprogramm. Es schützt Programme vor Reverse Engineering und macht sie gleichzeitig kleiner und effizienter.|  
  
## <a name="related-scenarios"></a>Ähnliche Szenarien  
 [Nutzen von Visual Studio und Team Foundation Server für Application Lifecycle Management](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 Wenn Sie mit Visual Studio Team Foundation nicht vertraut sind, erfahren Sie mehr zu dessen Verwendung in einer Teamentwicklungsumgebung, um die Produktivität zu steigern und um die Risiken zu minimieren, die mit der Anwendungsentwicklung einhergehen.  
  
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)  
 Sie können [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] verwenden, um die Herausforderungen und die Komplexität der Softwareentwicklung zu verwalten. Mit [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] können Sie die Anwendung visuell modellieren, sowohl im aktuellen Zustand als auch im gewünschten, künftigen Zustand. Sie können Diagramme erstellen und verwalten, die Ihnen bei der Visualisierung der logischen Modelle der Anwendung helfen und gleichzeitig eine Zuordnung zu den physischen Modellen herstellen. Dadurch sind Sie in der Lage, die im Entwurf befindliche Software zu ändern, zu überprüfen und zu analysieren.  
  
 [Testen der Anwendung](https://www.visualstudio.com/docs/test/overview)  
 Verwenden Sie [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] und [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)], um Ihre Produktivität für den gesamten Testlebenszyklus zu steigern. Mit [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] oder [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] planen Sie den Testaufwand. Sie können sowohl manuelle als auch automatisierte Tests erstellen, verwalten, bearbeiten und ausführen. Außerdem können Sie den Testfortschritt anhand Ihres Plans überprüfen.  
  
 [Erstellen der Anwendung](https://www.visualstudio.com/docs/build/overview)  
 Sie können [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] verwenden, um automatisierte Builds für den Code zu erstellen und zu verwalten. [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] ermöglicht das Erstellen von Ablageservern zum Bereitstellen von Builds. Außerdem können Sie Buildtrends analysieren.  
  
 [Nachverfolgen von Arbeit mit Visual Studio Online oder Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 Mithilfe von [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] können Sie Projekte planen und nachverfolgen, unabhängig davon, ob Sie den agilen Prozess, den formalen Prozess oder eine Variation dieser Prozesse verwenden. Indem Sie Ihre Projekte planen, den Status im Hinblick auf den Plan nachverfolgen und notwendige Anpassungen vornehmen, können Sie Risiken minimieren, unerfreuliche Überraschungen vermeiden und die Kosten der Projekte verwalten.
