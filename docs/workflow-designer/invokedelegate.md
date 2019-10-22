---
title: Workflow-Designer-invokedelegat
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650179"
---
# <a name="invokedelegate"></a>InvokeDelegate

Der **invokedelegatdesigner** wird verwendet, um eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-invokedelegate-activity"></a>Die invokedelegataktivität

<xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.

### <a name="use-the-invokedelegate-activity-designer"></a>Verwenden des invokedelegataktivitätsdesigners

Greifen Sie in der Kategorie **primitive** der **Toolbox**auf den **invokedelegatenaktivitäts** -Designer zu. Der **invokedelegataktivitätsdesigner** kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Beim Löschen des Aktivitäts Designers wird eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von invokedelegaten erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des invokedelegataktivitätsdesigners oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-invokedelegate-properties"></a>Die invokedelegeneigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen zu verwenden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft kann auf der Designer Oberfläche bearbeitet werden und ist obligatorisch.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Die Argumentauflistung des aufgerufenen Delegaten. Bei den Schlüsseln handelt es sich um die Namen der Parameter Objekte auf dem <xref:System.Activities.ActivityDelegate>, und die Werte sind die Argumente, deren Ausdrücke ausgewertet und den entsprechenden Parameter Objekten zugewiesen werden. Um das Dialogfeld **delegatearguments** anzuzeigen, in dem Sie diese Eigenschaft festlegen können, klicken Sie im Feld **delegatearguments** des Eigenschaften Rasters auf die Schaltfläche mit den Auslassungs Punkten. Klicken Sie auf das Feld **Argument erstellen** , um die Argumente hinzuzufügen.|

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)