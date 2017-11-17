---
title: "Interop-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3adc99e0a09d2d82049dcbe816f14b24ab48a55d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="interop-activity-designer"></a>Interop-Aktivitätsdesigner
Die **Interop** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Interop> Aktivität.  
  
## <a name="the-interop-activity"></a>Die Interop-Aktivität  
 Die <xref:System.Activities.Statements.Interop>-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.  
  
### <a name="using-the-interop-activity-designer"></a>Verwenden des Interop-Aktivitätsdesigners  
 Die **Interop** Aktivitäts-Designer finden Sie in der **Migration** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte (Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die [Migration](../workflow-designer/migration-activity-designers.md) Kategorie, enthält die <xref:System.Activities.Statements.Interop> Aktivität nur wird in der **Toolbox** Wenn Ihr Projekt die vollständige abzielt [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Für C#-Projekten können Sie erneut das Projekt, um die Zielplattform abzielen [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] durch Rechtsklick auf das Projekt in der **Projektmappen-Explorer** auswählen und **Eigenschaften**. Auf der **Anwendung** Registerkarte die **NET Framework 4** -Option in der **Zielframework**. Wählen Sie die **Ja** Schaltfläche der **Änderung des Zielframeworks** Dialogfeld, in dem Sie aufgefordert werden, diese Änderung zu bestätigen.  
  
 Für VB-Projekte können Sie das Projekt, um die Zielplattform erneut abzielen [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] mit der rechten Maustaste auf das Projekt in der **Projektmappen-Explorer** auswählen und **Eigenschaften**. Auf der **Kompilieren** Registerkarte, klicken Sie auf die **Erweiterte Kompilierungsoptionen** Schaltfläche. Wählen Sie **.Net Framework 4** aus der **Zielframeworkliste** , und klicken Sie dann auf **OK**. Klicken Sie auf die **Ja** Schaltfläche der **Änderung des Zielframeworks** Dialogfeld, in dem Sie aufgefordert werden, diese Änderung zu bestätigen.  
  
 Die **Interop** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.Interop> -Aktivität mit dem standardmäßigen **DisplayName** Interop. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Interop** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
 Klicken Sie auf die **klicken Sie auf Durchsuchen...**  Text in der **ActivityType** Feld entweder auf die **Interop** -Aktivitätsdesigner oder im Eigenschaftenraster, um die **.NET-Typ suchen und auswählen** Das Dialogfeld. Nur Typen für Workflow 3.0- oder Workflow 3.5-Aktivitäten werden angezeigt (d. h. nur Typen, die von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sind). [!INCLUDE[crabout](../test/includes/crabout_md.md)]Verwenden Sie dieses Kontrollkästchen zum Angeben eines Typs finden Sie unter der [navigieren, und wählen Sie ein Dialogfeld](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) Thema.  
  
### <a name="the-interop-properties"></a>Die Interop-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Interop>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Interop>-Aktivität. Der Standardwert lautet Interop. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>-Aktivität enthaltenen Aktivität an. Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|  
  
## <a name="see-also"></a>Siehe auch  
 [Migration](../workflow-designer/migration-activity-designers.md)