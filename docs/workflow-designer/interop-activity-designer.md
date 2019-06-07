---
title: Workflow-Designer - Interop-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688ef92fae5bd0cbaa5ddc653bbaab5692f4827f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747136"
---
# <a name="interop-activity-designer"></a>Interop-Aktivitätsdesigner

Die **Interop** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Interop> Aktivität.

## <a name="the-interop-activity"></a>Die Interop-Aktivität

Die <xref:System.Activities.Statements.Interop>-Aktivität verwaltet die Ausführung von Typen, die sich von <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> innerhalb eines Workflows ableiten.

### <a name="use-the-interop-activity-designer"></a>Verwenden des Interop-Aktivitätsdesigners

Die **Interop** Aktivitäts-Designer finden Sie in der **Migration** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte. Sie können auch **Toolbox** aus der **anzeigen** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

Die [Migration](../workflow-designer/migration-activity-designers.md) Kategorie, enthält die <xref:System.Activities.Statements.Interop> Aktivität erscheint nur in **Toolbox** Wenn das Projekt .NET Framework 4 (vollständig) verwendet oder höher. Wenn erforderlich, Sie die Framework-Version ändern können, die das Projekt abzielt.

Die **Interop** Aktivitäts-Designer gezogen werden kann, von **Toolbox** und auf die Oberfläche des Workflow-Designer gelöscht werden, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen der **Interop** Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.Interop> -Aktivität mit dem standardmäßigen **"DisplayName"** von Interop. Können Sie bearbeiten die <xref:System.Activities.Activity.DisplayName%2A> im Header des der **Interop** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

Klicken Sie auf die **zum Durchsuchen klicken** Text in die **ActivityType** Feld, auf die **Interop** -Aktivitätsdesigner oder im Eigenschaftenraster zu öffnen der **durchsuchen und Wählen Sie eine .net Typ** Dialogfeld. Nur Typen für Workflow 3.0- oder Workflow 3.5-Aktivitäten werden angezeigt. D. h. nur Typen abgeleitet von <xref:System.Workflow.ComponentModel.Activity> werden angezeigt. Weitere Informationen zur Verwendung dieses Dialogfelds zum Angeben eines Typs finden Sie unter [navigieren, und wählen Sie ein Dialogfeld](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Die Interop-Eigenschaften

Die folgende Tabelle zeigt die <xref:System.Activities.Statements.Interop> Eigenschaften, und beschreibt, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Interop>-Aktivität. Der Standardwert ist **Interop**. Obwohl der Anzeigename nicht erforderlich ist, wird empfohlen, einen bereitzustellen.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Gibt den Typ der in der <xref:System.Activities.Statements.Interop>-Aktivität enthaltenen Aktivität an. Der angegebene Typ muss von <xref:System.Workflow.ComponentModel.Activity> abgeleitet sein.|

## <a name="see-also"></a>Siehe auch

- [Migration](../workflow-designer/migration-activity-designers.md)