---
title: Workflow-Designer Interop-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650212"
---
# <a name="interop-activity-designer"></a>Interop-Aktivitätsdesigner

Der **Interop** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Interop>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-interop-activity"></a>Die Interop-Aktivität

Die <xref:System.Activities.Statements.Interop>-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.

### <a name="use-the-interop-activity-designer"></a>Verwenden des Interop-Aktivitäts Designers

Der **Interop** -Aktivitäts Designer befindet sich in der Kategorie **Migration** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken. Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG drücken.+**alt** +**X**.

Die Kategorie [Migration](../workflow-designer/migration-activity-designers.md) , in der die <xref:System.Activities.Statements.Interop> Aktivität enthalten ist, wird nur in **Toolbox** angezeigt, wenn Ihr Projekt auf .NET Framework 4 (Full) oder höher ausgerichtet ist. Falls erforderlich, können Sie die Frameworkversion ändern, auf die Ihr Projekt abzielt.

Der **Interop** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Beim Löschen des **Interop** -Aktivitäts Designers wird eine <xref:System.Activities.Statements.Interop>-Aktivität mit dem standardmäßigen **Display Name** Interop erstellt. Sie können die <xref:System.Activities.Activity.DisplayName%2A> in der Kopfzeile des **Interop** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeiten.

Klicken Sie entweder im **Interop** -Aktivitäts Designer oder im Eigenschaften Raster auf den Text zum **Durchsuchen** von Text, um das Dialogfeld **.NET-Typ suchen und auswählen** zu öffnen. Es werden nur Typen für Workflow 3,0-oder Workflow 3,5-Aktivitäten angezeigt. Das heißt, dass nur von <xref:System.Workflow.ComponentModel.Activity> abgeleitete Typen angezeigt werden. Weitere Informationen zur Verwendung dieses Felds zum Angeben eines Typs finden Sie unter [Durchsuchen und Auswählen eines .net-Typs (Dialog Feld](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)).

### <a name="the-interop-properties"></a>Die Interop-Eigenschaften

In der folgenden Tabelle sind die <xref:System.Activities.Statements.Interop> Eigenschaften aufgeführt, und es wird beschrieben, wie Sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster oder auf der Workflow-Designer-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Interop>-Aktivität. Der Standardwert ist **Interop**. Obwohl der Anzeige Name nicht erforderlich ist, wird empfohlen, einen anzugeben.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>-Aktivität enthaltenen Aktivität an. Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|

## <a name="see-also"></a>Siehe auch

- [Migration](../workflow-designer/migration-activity-designers.md)