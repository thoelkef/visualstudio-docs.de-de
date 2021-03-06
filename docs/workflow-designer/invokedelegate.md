---
title: Workflow-Designer-invokedelegat
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: 9e63fb7a766b79467749cc5181a575e0d35a07b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876072"
---
# <a name="invokedelegate"></a>InvokeDelegate

Der **invokedelegatdesigner** wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.InvokeDelegate> .

## <a name="the-invokedelegate-activity"></a>Die invokedelegataktivität

<xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.

### <a name="use-the-invokedelegate-activity-designer"></a>Verwenden des invokedelegataktivitätsdesigners

Greifen Sie in der Kategorie **primitive** der **Toolbox**auf den **invokedelegatenaktivitäts** -Designer zu. Der **invokedelegataktivitätsdesigner** kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Beim Löschen des Aktivitäts Designers wird eine <xref:System.Activities.Statements.InvokeDelegate> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> invokedelegat erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des invokedelegataktivitätsdesigners oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. **InvokeDelegate**

### <a name="the-invokedelegate-properties"></a>Die invokedelegeneigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht unbedingt erforderlich ist, empfiehlt es sich, einen zu verwenden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Richtig|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft kann auf der Designer Oberfläche bearbeitet werden und ist obligatorisch.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falsch|Die Argumentauflistung des aufgerufenen Delegaten. Bei den Schlüsseln handelt es sich um die Namen der Parameter Objekte in der <xref:System.Activities.ActivityDelegate> , und die Werte sind die Argumente, deren Ausdrücke ausgewertet und den entsprechenden Parameter Objekten zugewiesen werden. Um das Dialogfeld **delegatearguments** anzuzeigen, in dem Sie diese Eigenschaft festlegen können, klicken Sie im Feld **delegatearguments** des Eigenschaften Rasters auf die Schaltfläche mit den Auslassungs Punkten. Klicken Sie auf das Feld **Argument erstellen** , um die Argumente hinzuzufügen.|

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)