---
title: InvokeDelegate | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961634"
---
# <a name="invokedelegate"></a>InvokeDelegate

Die **InvokeDelegate** -Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.InvokeDelegate> Aktivität.

## <a name="the-invokedelegate-activity"></a>Die InvokeDelegate-Aktivität

<xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.

### <a name="using-the-invokedelegate-activity-designer"></a>Verwenden des InvokeDelegate-Aktivitäts-Designers

Die **InvokeDelegate** Aktivitäts-Designer finden Sie in der **primitive** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** Registerkarte [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü oder STRG + ALT + X.)

Die **InvokeDelegate** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche, wo Aktivitäten normalerweise platziert, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert InvokeDelegate erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InvokeDelegate** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-invokedelegate-properties"></a>Die InvokeDelegate-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Dies ist eine obligatorische Eigenschaft.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Die Argumentauflistung des aufgerufenen Delegaten. Die Schlüssel sind die Namen der <xref:System.Activities.DelegateArgument>-Objekte auf dem <xref:System.Activities.ActivityDelegate>, und die Werte sind die Argumente, deren Ausdrücke ausgewertet werden und den entsprechenden <xref:System.Activities.DelegateArgument>-Objekten zugewiesen werden. Klicken Sie im Eigenschaftenraster auf die Schaltfläche mit den Auslassungspunkten, in der **DelegateArguments** -Feld die **DelegateArguments** Dialogfeld Sie diese Eigenschaft festlegen können. Klicken Sie auf die **Argument erstellen** Feld, um die Argumente hinzuzufügen.|

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)