---
title: Interop-Aktivitätsdesigner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956939"
---
# <a name="interop-activity-designer"></a>Interop-Aktivitätsdesigner
Die **Interop** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Interop> Aktivität.  
  
## <a name="the-interop-activity"></a>Die Interop-Aktivität  
 Die <xref:System.Activities.Statements.Interop>-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.  
  
### <a name="using-the-interop-activity-designer"></a>Verwenden des Interop-Aktivitätsdesigners  
 Die **Interop** Aktivitäts-Designer finden Sie in der **Migration** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die [Migration](../workflow-designer/migration-activity-designers.md) Kategorie, enthält die <xref:System.Activities.Statements.Interop> Aktivität nur wird in der **Toolbox** Wenn Ihr Projekt, das vollständige abzielt [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Für c#-Projekten können Sie erneut das Projekt, um die Verwendung des vollständigen anwenden [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] durch Rechtsklick auf das Projekt in der **Projektmappen-Explorer** und **Eigenschaften**. Auf der **Anwendung** Registerkarte die **.NET Framework 4** option die **Zielframework**. Wählen Sie die **Ja** Schaltfläche der **Änderung des Zielframeworks** Dialogfeld, in dem Sie aufgefordert werden, die diese Änderung zu bestätigen.  
  
 Für VB-Projekte können Sie das Projekt, um die Verwendung des vollständigen erneut anwenden [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] mit der rechten Maustaste auf das Projekt in der **Projektmappen-Explorer** und **Eigenschaften**. Auf der **Kompilieren** Registerkarte, klicken Sie auf die **Advanced Compile Options** Schaltfläche. Wählen Sie **.Net Framework 4** aus der **Zielframeworkliste** , und klicken Sie dann auf **OK**. Klicken Sie auf die **Ja** Schaltfläche der **Änderung des Zielframeworks** Dialogfeld, in dem Sie aufgefordert werden, die diese Änderung zu bestätigen.  
  
 Die **Interop** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Interop> -Aktivität mit dem standardmäßigen **"DisplayName"** von Interop. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Interop** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.  
  
 Klicken Sie auf die **zum Durchsuchen klicken...** Text in die **ActivityType** Feld, auf die **Interop** -Aktivitätsdesigner oder im Eigenschaftenraster, um die **.NET-Typ suchen und auswählen** Dialogfeld. Nur Typen für Workflow 3.0- oder Workflow 3.5-Aktivitäten werden angezeigt (d. h. nur Typen, die von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sind). [!INCLUDE[crabout](../includes/crabout-md.md)] Verwenden Sie dieses Kontrollkästchen zum Angeben eines Typs, finden Sie unter den [navigieren, und wählen Sie ein Dialogfeld](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) Thema.  
  
### <a name="the-interop-properties"></a>Die Interop-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Interop>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Interop>-Aktivität. Der Standardwert lautet Interop. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>-Aktivität enthaltenen Aktivität an. Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|  
  
## <a name="see-also"></a>Siehe auch  
 [Migration](../workflow-designer/migration-activity-designers.md)