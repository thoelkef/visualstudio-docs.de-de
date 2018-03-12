---
title: Entwickeln von Anwendungen mit dem Workflow-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 75a6fb6eef1f5e8e174607ac141646ab237dd285
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Entwickeln von Anwendungen mit dem Workflow-Designer

Windows Workflow-Designer ist ein visueller Designer und Debugger zum grafischen Aufbau und debugging von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen in der [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] , gehostet wird, der [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Entwicklungsumgebung. Er ermöglicht es Ihnen, durch die Verwendung von Vorlagen und Aktivitätsdesignern eine zusammengesetzte Workflowanwendung, eine Aktivitätsbibliothek oder einen [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]-Dienst zu erstellen. Weitere Informationen zu Workflows finden Sie unter der [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Im Folgenden werden einige neue Entwurfsfunktionen aufgeführt, durch die sich diese neue Version von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] von früheren Versionen von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] unterscheidet:

-   Der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] wird mit [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)] erstellt. Dadurch wird die Handhabung des Aktivitätsdesigners und die Leistung bei großen und komplexen Workflows verbessert.

-   Benutzerdefinierte Aktivitäten werden jetzt mit [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] in XAML entworfen, und das Programmiermodell zum Erstellen der Aktivitätsdesigner wurde vereinfacht.

-   Es wurde eine Flussdiagrammaktivität implementiert, damit Sie den Programmablauf mit dem vertrauten Flussdiagrammmodellierungsformat visuell darstellen können.

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verfügt über einen neuen variablen Designer, der es Ihnen ermöglicht, Variablen innerhalb der Workflows zu deklarieren und deren Bereich festzulegen, indem Sie sie an Aktivitäten binden.

-   In [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] bietet der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] umfassende IntelliSense-Funktionen beim Erstellen von Visual Basic-Ausdrücken innerhalb von [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]-Workflows.

-   Die Debugfunktion wurde erweitert und ermöglicht es Ihnen, Haltepunkte in der XAML-Workflowdefinition festzulegen und den XAML-Code zur Laufzeit schrittweise auszuführen, sodass XAML ähnlich wie verwalteter Code im Debugger bearbeitet werden kann.

-   Erneutes Hosting von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] außerhalb [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist gegenüber früheren Versionen viel einfacher und erfordert jetzt nur einige Codezeile.

-   Die neue <xref:System.Activities.Statements.Flowchart> Aktivität und die zugehörige [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) ermöglichen es Ihnen, Ihre Programmablauf, die mit dem vertrauten flussdiagrammmodellierungsformat visuell darstellen.

-   Die Messagingaktivitäten wurden verbessert, sodass Sie vollständig-deklarative (kein Code) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]-Dienste schreiben können.

-   Die **Dienstverweis hinzufügen...**  Funktionalität bietet die Möglichkeit zum Generieren von Aktivitäten automatisch, die Webdienste greifen auf.