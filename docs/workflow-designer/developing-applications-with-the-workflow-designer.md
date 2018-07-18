---
title: Entwickeln von Anwendungen mit dem Workflow-Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970124"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Entwickeln von Anwendungen mit dem Workflow-Designer

Windows Workflow-Designer ist ein visueller Designer und Debugger zum grafischen Aufbau und Debuggen von Windows Workflow Foundation (WF)-Anwendungen in .NET Framework 4, die in der Visual Studio 2010-Entwicklungsumgebung gehostet wird. Er ermöglicht es Ihnen, eine zusammengesetzte workflowanwendung, Aktivitätsbibliothek oder Windows Communication Foundation (WCF)-Dienst durch die Verwendung von Vorlagen und Aktivitätsdesignern zu verfassen. Weitere Informationen zu Workflows finden Sie unter der [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Es folgen einige neue Entwurfsfunktionen, die diese neue Version im Workflow-Designer, abgesehen von älteren Versionen von Workflow-Designer festgelegt:

-   Workflow-Designer wird mithilfe von Windows Presentation Foundation (WPF) erstellt. Dadurch wird die Handhabung des Aktivitätsdesigners und die Leistung bei großen und komplexen Workflows verbessert.

-   Benutzerdefinierte Aktivitäten werden jetzt mit [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)] in XAML entworfen, und das Programmiermodell zum Erstellen der Aktivitätsdesigner wurde vereinfacht.

-   Es wurde eine Flussdiagrammaktivität implementiert, damit Sie den Programmablauf mit dem vertrauten Flussdiagrammmodellierungsformat visuell darstellen können.

-   Workflow-Designer verfügt über einen neuen Variablen Designer, mit dem Sie deklariert werden und der Bereichsvariablen innerhalb der Workflows, indem sie an Aktivitäten binden.

-   In Visual Studio 2010 stellt die Workflow-Designer umfassende IntelliSense-Funktionen, beim Erstellen von Visual Basic-Ausdrücke innerhalb der .NET Framework 4-Workflows.

-   Die Debugfunktion wurde erweitert und ermöglicht es Ihnen, Haltepunkte in der XAML-Workflowdefinition festzulegen und den XAML-Code zur Laufzeit schrittweise auszuführen, sodass XAML ähnlich wie verwalteter Code im Debugger bearbeitet werden kann.

-   Erneutes Hosten des Workflow-Designers außerhalb von Visual Studio ist stark vereinfacht im Vergleich zu früheren Versionen erfordert jetzt nur wenige Codezeilen.

-   Die neue <xref:System.Activities.Statements.Flowchart> Aktivität und die zugehörige [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) ermöglichen es Ihnen, Ihre Programmablauf, die mit dem vertrauten flussdiagrammmodellierungsformat visuell darstellen.

-   Die messagingaktivitäten wurden verbessert, sodass Ihnen das Schreiben vollständig-deklarative (kein Code) Windows Communication Foundation (WCF)-Dienste.

-   Die **Dienstverweis hinzufügen...**  Funktionalität bietet die Möglichkeit zum Generieren von Aktivitäten automatisch, die Webdienste greifen auf.