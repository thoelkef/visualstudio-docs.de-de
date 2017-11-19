---
title: Entwickeln von Anwendungen mit dem Workflow-Designer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: cbb7b09e5c36980ceeedd99f69241996bd25bfa3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Entwickeln von Anwendungen mit dem Workflow-Designer
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] ist ein visueller Designer und Debugger zum grafischen Aufbau und Debugging von  [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen im [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)], das in der [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Entwicklungsumgebung gehostet wird. Er ermöglicht es Ihnen, durch die Verwendung von Vorlagen und Aktivitätsdesignern eine zusammengesetzte Workflowanwendung, eine Aktivitätsbibliothek oder einen [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]-Dienst zu erstellen. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Workflows, finden Sie unter der [Windows Workflow Foundation &#91;. NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
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
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)  
 Zeigt, wie neue Aktivitäten und Workflowprojekte mithilfe der integrierten Designer erstellt werden, und wie andere vom Designer bereitgestellte Tools verwendet werden, um Argumente, Variablen, Ausdrücke, Importe und Breadcrumbnavigation zu verarbeiten.  
  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)  
 Beschreibt die Kategorien der Aktivitäten und Vorlagen und ihre vom System bereitgestellten Designer.  
  
 [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Beschreibt die herkömmlichen Debugverfahren sowie das Debuggen von XAML und Ausdrücken.  
  
 [Workflow-Designer-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)  
 Enthält kontextbezogene Hilfethemen für von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] bereitgestellte Dialogfelder sowie Anleitungen zu Designer-Shellfunktionen, Tastenkombinationen und Fehlermeldungen.  
  
 [Entwickeln von Workflowanwendungen, die auf .NET 3.0 oder .NET auf 3.5 Framework abzielen](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Enthält Anleitungen zur Verwendung des Designers der Vorgängerversion, der auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 [Hosten von Designern &#91; WF-Beispiele &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 In diesem Beispiel wird gezeigt, wie das WPF-Layout erstellt wird, das den Designer enthalten soll.  
  
 [Benutzerdefinierte Aktivitätsdesigner](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 Dieser Abschnitt enthält Aktivitätsbeispiele, in denen benutzerdefinierte Designer zur Anzeige im Workflow-Designer verwendet werden.