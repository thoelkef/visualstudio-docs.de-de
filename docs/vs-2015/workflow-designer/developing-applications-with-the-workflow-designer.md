---
title: Entwickeln von Anwendungen mit Workflow-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9eea79978b7b61de1e56d787b5a4cd9797be1aa6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704784"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Entwickeln von Anwendungen mit dem Workflow-Designer
[!INCLUDE[wfd1](../includes/wfd1-md.md)] ist ein visueller Designer und Debugger zum grafischen Aufbau und Debugging von  [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen im [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)], das in der [!INCLUDE[vs2010](../includes/vs2010-md.md)] Entwicklungsumgebung gehostet wird. Er ermöglicht es Ihnen, durch die Verwendung von Vorlagen und Aktivitätsdesignern eine zusammengesetzte Workflowanwendung, eine Aktivitätsbibliothek oder einen [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Dienst zu erstellen. [!INCLUDE[crabout](../includes/crabout-md.md)] finden Sie unter den [Windows Workflow Foundation &#91;.NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Im Folgenden werden einige neue Entwurfsfunktionen aufgeführt, durch die sich diese neue Version von [!INCLUDE[wfd2](../includes/wfd2-md.md)] von früheren Versionen von [!INCLUDE[wfd2](../includes/wfd2-md.md)] unterscheidet:  
  
- Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird mit [!INCLUDE[avalon1](../includes/avalon1-md.md)] erstellt. Dadurch wird die Handhabung des Aktivitätsdesigners und die Leistung bei großen und komplexen Workflows verbessert.  
  
- Benutzerdefinierte Aktivitäten werden jetzt mit [!INCLUDE[avalon2](../includes/avalon2-md.md)] in XAML entworfen, und das Programmiermodell zum Erstellen der Aktivitätsdesigner wurde vereinfacht.  
  
- Es wurde eine Flussdiagrammaktivität implementiert, damit Sie den Programmablauf mit dem vertrauten Flussdiagrammmodellierungsformat visuell darstellen können.  
  
- [!INCLUDE[wfd2](../includes/wfd2-md.md)] verfügt über einen neuen variablen Designer, der es Ihnen ermöglicht, Variablen innerhalb der Workflows zu deklarieren und deren Bereich festzulegen, indem Sie sie an Aktivitäten binden.  
  
- In [!INCLUDE[vs2010](../includes/vs2010-md.md)] bietet der [!INCLUDE[wfd2](../includes/wfd2-md.md)] umfassende IntelliSense-Funktionen beim Erstellen von Visual Basic-Ausdrücken innerhalb von [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]-Workflows.  
  
- Die Debugfunktion wurde erweitert und ermöglicht es Ihnen, Haltepunkte in der XAML-Workflowdefinition festzulegen und den XAML-Code zur Laufzeit schrittweise auszuführen, sodass XAML ähnlich wie verwalteter Code im Debugger bearbeitet werden kann.  
  
- Erneutes Hosting von [!INCLUDE[wfd2](../includes/wfd2-md.md)] außerhalb [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist gegenüber früheren Versionen viel einfacher und erfordert jetzt nur einige Codezeile.  
  
- Die neue <xref:System.Activities.Statements.Flowchart> Aktivität und die zugehörige [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) können Sie den Programmablauf mit dem vertrauten flussdiagrammmodellierungsformat visuell darstellen.  
  
- Die Messagingaktivitäten wurden verbessert, sodass Sie vollständig-deklarative (kein Code) [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Dienste schreiben können.  
  
- Die **Dienstverweis hinzufügen...** Funktionalität ermöglicht es Ihnen, Aktivitäten automatisch, die Zugriff auf Webdienste zu generieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden des Workflow-Designers](../workflow-designer/using-the-workflow-designer.md)  
 Zeigt, wie neue Aktivitäten und Workflowprojekte mithilfe der integrierten Designer erstellt werden, und wie andere vom Designer bereitgestellte Tools verwendet werden, um Argumente, Variablen, Ausdrücke, Importe und Breadcrumbnavigation zu verarbeiten.  
  
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)  
 Beschreibt die Kategorien der Aktivitäten und Vorlagen und ihre vom System bereitgestellten Designer.  
  
 [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Beschreibt die herkömmlichen Debugverfahren sowie das Debuggen von XAML und Ausdrücken.  
  
 [Workflow-Designer-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)  
 Enthält kontextbezogene Hilfethemen für von [!INCLUDE[wfd1](../includes/wfd1-md.md)] bereitgestellte Dialogfelder sowie Anleitungen zu Designer-Shellfunktionen, Tastenkombinationen und Fehlermeldungen.  
  
 [Entwickeln von Workflowanwendungen, die auf .NET 3.0 oder .NET auf 3.5 Framework abzielen](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Enthält Anleitungen zur Verwendung des Designers der Vorgängerversion, der auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
 [Designer betreffen &#91;WF-Beispiele&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 In diesem Beispiel wird gezeigt, wie das WPF-Layout erstellt wird, das den Designer enthalten soll.  
  
 [Benutzerdefinierte Aktivitätsdesigner](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 Dieser Abschnitt enthält Aktivitätsbeispiele, in denen benutzerdefinierte Designer zur Anzeige im Workflow-Designer verwendet werden.