---
title: Interop-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659035"
---
# <a name="interop-activity-designer"></a>Interop-Aktivitätsdesigner
Der **Interop** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.Interop> .

## <a name="the-interop-activity"></a>Die Interop-Aktivität
 Die <xref:System.Activities.Statements.Interop>-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.

### <a name="using-the-interop-activity-designer"></a>Verwenden des Interop-Aktivitätsdesigners
 Der **Interop** -Aktivitäts Designer befindet sich in der Kategorie **Migration** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG + ALT + X drücken).

 Die Kategorie [Migration](../workflow-designer/migration-activity-designers.md) , in der die- <xref:System.Activities.Statements.Interop> Aktivität enthalten ist, wird nur in der **Toolbox** angezeigt, wenn Ihr Projekt auf den vollständigen abzielt [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 Für c#-Projekte können Sie das Projekt so neu ausrichten, dass es den vollständigen verwendet, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften**auswählen. Wählen Sie auf der Registerkarte **Anwendung** die Option **NET Framework 4** im **Ziel Framework**aus. Wählen Sie im Dialogfeld **Ziel Framework-Änderung** die Schaltfläche **Ja** aus, in der Sie aufgefordert werden, diese Änderung zu bestätigen.

 Für VB-Projekte können Sie das Projekt erneut als Ziel verwenden, indem Sie [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften**auswählen. Klicken Sie auf der Registerkarte **Kompilieren** auf die Schaltfläche **Erweiterte Kompilierungsoptionen** . Wählen Sie **.NET Framework 4** aus der **Liste Ziel Framework** aus, und klicken Sie dann auf **OK**. Klicken Sie im Dialogfeld **Ziel Framework-Änderung** auf die Schaltfläche **Ja** , in der Sie aufgefordert werden, diese Änderung zu bestätigen.

 Der **Interop** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence> . Dadurch wird eine <xref:System.Activities.Statements.Interop> Aktivität mit dem **Display Name** -Standardwert Interop erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **Interop** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

 Klicken Sie auf die Schaltfläche **zum Durchsuchen...** Text im Feld **ActivityType** , entweder im **Interop**  -Aktivitäts Designer oder im Eigenschaften Raster, um das Dialogfeld **.NET-Typ suchen und auswählen** zu aktivieren. Nur Typen für Workflow 3.0- oder Workflow 3.5-Aktivitäten werden angezeigt (d. h. nur Typen, die von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sind). [!INCLUDE[crabout](../includes/crabout-md.md)] in diesem Feld können Sie einen Typ angeben. Weitere Informationen hierzu finden Sie im Thema zum [Durchsuchen und Auswählen eines .net-Typs](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Die Interop-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Interop>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.Interop>-Aktivität. Der Standardwert lautet Interop. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Richtig|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>-Aktivität enthaltenen Aktivität an. Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|

## <a name="see-also"></a>Weitere Informationen
 [Migration](../workflow-designer/migration-activity-designers.md)