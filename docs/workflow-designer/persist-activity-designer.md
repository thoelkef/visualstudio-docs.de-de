---
title: Workflow-Designer-persistenzdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882a68e006ac139d717320b0b8b7ce4d75aceb38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650117"
---
# <a name="persist-activity-designer"></a>Persist-Aktivitätsdesigners

Der **persistenzaktivitäts** -Designer wird verwendet, um eine <xref:System.Activities.Statements.Persist> Aktivität zu erstellen und zu konfigurieren.

## <a name="the-persist-activity"></a>Die Persist-Aktivität

Wenn möglich, speichert die <xref:System.Activities.Statements.Persist>-Aktivität einen Workflow auf dem Datenträger. Die <xref:System.Activities.Statements.Persist>-Aktivität kann nicht in einem Bereich ohne Persistenz ausgeführt werden, z. B. innerhalb einer <xref:System.Activities.Statements.TransactionScope>-Aktivität. Wenn Sie eine <xref:System.Activities.Statements.Persist> Aktivität in einem Bereich ohne Persistenz verwenden, wird zur Laufzeit eine Ausnahme ausgelöst.

### <a name="using-the-persist-activity-designer"></a>Verwenden des Persist-Aktivitätsdesigners

Der persistenzaktivitätsdesigner befindet sich in der Kategorie **Laufzeit** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG + ALT + X drücken).

Der persistenzaktivitätsdesigner kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Persist>-Aktivität mit dem **Display Name** -Standardwert persistent erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im **Header des persistenten Aktivitäts Designers** oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-persist-properties"></a>Die Persist-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.Persist>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige von Ihnen können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Persist>-Aktivität. Der Standardwert lautet Persist. Obwohl der Anzeigename nicht unbedingt erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|

## <a name="see-also"></a>Siehe auch

- [Laufzeit](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)