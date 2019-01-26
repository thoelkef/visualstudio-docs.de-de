---
title: Workflow-Designer - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d960984ddb65069b5d8ccd489ed3831d6c11b33c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967705"
---
# <a name="invokedelegate"></a>InvokeDelegate

Die **InvokeDelegate** -Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.InvokeDelegate> Aktivität.

## <a name="the-invokedelegate-activity"></a>Die InvokeDelegate-Aktivität

<xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.

### <a name="use-the-invokedelegate-activity-designer"></a>Verwenden des InvokeDelegate-Aktivitäts-Designers

Zugriff die **InvokeDelegate** Aktivitäts-Designer in der **primitive** Kategorie der **Toolbox**. Die **InvokeDelegate** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, egal wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen die Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.InvokeDelegate> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> -Standardwert InvokeDelegate. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InvokeDelegate** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-invokedelegate-properties"></a>Die InvokeDelegate-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige auf die Oberfläche des Workflow-Designer bearbeitet werden kann.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl die <xref:System.Activities.Activity.DisplayName%2A> ist nicht zwingend erforderlich, es wird empfohlen, einen verwenden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft auf der Designeroberfläche bearbeitet werden kann, und es ist zwingend erforderlich.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Die Argumentauflistung des aufgerufenen Delegaten. Die Schlüssel sind die Namen der Parameterobjekte, auf die <xref:System.Activities.ActivityDelegate>, und die Werte sind die Argumente, deren Ausdrücke ausgewertet und die entsprechenden Parameterobjekte zugewiesen sind. Zum Anzeigen der **DelegateArguments** Dialogfeld, in dem Sie diese Eigenschaft festlegen können, klicken Sie auf die Schaltfläche mit den Auslassungspunkten, in der **DelegateArguments** Feld des Eigenschaftenrasters. Klicken Sie auf die **Argument erstellen** Feld, um die Argumente hinzuzufügen.|

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Definieren und Verarbeiten von aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)