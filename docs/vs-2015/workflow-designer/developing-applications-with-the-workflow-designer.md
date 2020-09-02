---
title: Entwickeln von Anwendungen mit dem Workflow-Designer | Microsoft-Dokumentation
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656828"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Entwickeln von Anwendungen mit dem Workflow-Designer
[!INCLUDE[wfd1](../includes/wfd1-md.md)] ist ein visueller Designer und Debugger zum grafischen Aufbau und Debugging von  [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen im [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)], das in der [!INCLUDE[vs2010](../includes/vs2010-md.md)] Entwicklungsumgebung gehostet wird. Er ermöglicht es Ihnen, durch die Verwendung von Vorlagen und Aktivitätsdesignern eine zusammengesetzte Workflowanwendung, eine Aktivitätsbibliothek oder einen [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Dienst zu erstellen. [!INCLUDE[crabout](../includes/crabout-md.md)] zu Workflows finden Sie in der [Windows Workflow Foundation &#91; .NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Im Folgenden werden einige neue Entwurfsfunktionen aufgeführt, durch die sich diese neue Version von [!INCLUDE[wfd2](../includes/wfd2-md.md)] von früheren Versionen von [!INCLUDE[wfd2](../includes/wfd2-md.md)] unterscheidet:

- Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird mit [!INCLUDE[avalon1](../includes/avalon1-md.md)] erstellt. Dadurch wird die Handhabung des Aktivitätsdesigners und die Leistung bei großen und komplexen Workflows verbessert.

- Benutzerdefinierte Aktivitäten werden jetzt mit [!INCLUDE[avalon2](../includes/avalon2-md.md)] in XAML entworfen, und das Programmiermodell zum Erstellen der Aktivitätsdesigner wurde vereinfacht.

- Es wurde eine Flussdiagrammaktivität implementiert, damit Sie den Programmablauf mit dem vertrauten Flussdiagrammmodellierungsformat visuell darstellen können.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] verfügt über einen neuen variablen Designer, der es Ihnen ermöglicht, Variablen innerhalb der Workflows zu deklarieren und deren Bereich festzulegen, indem Sie sie an Aktivitäten binden.

- In [!INCLUDE[vs2010](../includes/vs2010-md.md)] bietet der [!INCLUDE[wfd2](../includes/wfd2-md.md)] umfassende IntelliSense-Funktionen beim Erstellen von Visual Basic-Ausdrücken innerhalb von [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]-Workflows.

- Die Debugfunktion wurde erweitert und ermöglicht es Ihnen, Haltepunkte in der XAML-Workflowdefinition festzulegen und den XAML-Code zur Laufzeit schrittweise auszuführen, sodass XAML ähnlich wie verwalteter Code im Debugger bearbeitet werden kann.

- Erneutes Hosting von [!INCLUDE[wfd2](../includes/wfd2-md.md)] außerhalb [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist gegenüber früheren Versionen viel einfacher und erfordert jetzt nur einige Codezeile.

- Mithilfe der neuen <xref:System.Activities.Statements.Flowchart> -Aktivität und des zugehörigen [Fluss Diagramms](../workflow-designer/flowchart-activity-designer.md) können Sie den Programmablauf mit dem vertrauten Flussdiagramm Modellierungs Stil visualisieren.

- Die Messagingaktivitäten wurden verbessert, sodass Sie vollständig-deklarative (kein Code) [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Dienste schreiben können.

- Der **Dienstverweis hinzufügen...** mit der-Funktion können Sie automatisch Aktivitäten generieren, die auf Webdienste zugreifen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Verwenden des Workflow-Designer](../workflow-designer/using-the-workflow-designer.md) Zeigt, wie neue Aktivitäten und Workflow Projekte mithilfe der integrierten Designer erstellt werden und wie andere vom Designer bereitgestellte Tools verwendet werden, um Argumente, Variablen, Ausdrücke, Importe und Breadcrumb-Navigation zu verarbeiten.

 [Verwenden der Aktivitäts Designer](../workflow-designer/using-the-activity-designers.md) Beschreibt die Kategorien von Aktivitäten und Vorlagen und deren Designer, die vom System bereitgestellt werden.

 [Debuggen von Workflows mit dem Workflow-Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Beschreibt, wie herkömmliche Debugprozeduren durchgeführt werden und wie XAML und Ausdrücke debuggt werden.

 [Workflow-Designer UI-Hilfe](../workflow-designer/workflow-designer-ui-help.md) Enthält kontextbezogene Hilfe Themen für Dialogfelder, die von bereitgestellt werden [!INCLUDE[wfd1](../includes/wfd1-md.md)] , sowie Anleitungen zu Designer-Shellfeatures, Tastenkombinationen und Fehlermeldungen.

 [Entwickeln von Workflow Anwendungen, die auf .NET 3,0 oder .NET 3,5 Framework abzielen](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Enthält Anleitungen zur Verwendung des Legacy-Designers, der auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder abzielt [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [Designer Rehosting &#91;WF-Beispiele&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) In diesem Beispiel wird gezeigt, wie das WPF-Layout erstellt wird, um den Designer zu enthalten.

 [Benutzerdefinierte Aktivitäts Designer](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Dieser Abschnitt enthält Aktivitäts Beispiele, in denen benutzerdefinierte Designer zur Anzeige im Workflow-Designer verwendet werden.