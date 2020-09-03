---
title: Invokedelegat | Microsoft-Dokumentation
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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659003"
---
# <a name="invokedelegate"></a>InvokeDelegate

Der **invokedelegatdesigner** wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.InvokeDelegate> .

## <a name="the-invokedelegate-activity"></a>Die InvokeDelegate-Aktivität

<xref:System.Activities.Statements.InvokeDelegate> ruft einen öffentlichen Delegaten auf.

### <a name="using-the-invokedelegate-activity-designer"></a>Verwenden des InvokeDelegate-Aktivitäts-Designers

Der **invokedelegataktivitätsdesigner** befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder Crtl + ALT + X auswählen.)

Der **invokedelegataktivitätsdesigner** kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Daraufhin wird eine <xref:System.Activities.Statements.InvokeDelegate>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert InvokeDelegate erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des invokedelegataktivitätsdesigners oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. **InvokeDelegate**

### <a name="the-invokedelegate-properties"></a>Die InvokeDelegate-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.InvokeDelegate>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, einige davon können auch in der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Designeroberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.InvokeDelegate>-Aktivität. Der Standardwert lautet InvokeDelegate.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Richtig|Der Name des <xref:System.Activities.ActivityDelegate>, der bei Ausführung der Aktivität aufgerufen werden soll. Diese Eigenschaft kann in der Designeroberfläche bearbeitet werden. Dies ist eine obligatorische Eigenschaft.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Falsch|Die Argumentauflistung des aufgerufenen Delegaten. Die Schlüssel sind die Namen der <xref:System.Activities.DelegateArgument>-Objekte auf dem <xref:System.Activities.ActivityDelegate>, und die Werte sind die Argumente, deren Ausdrücke ausgewertet werden und den entsprechenden <xref:System.Activities.DelegateArgument>-Objekten zugewiesen werden. Klicken Sie im Eigenschaften Raster im Feld **delegatearguments** auf die Schaltfläche mit den Auslassungs Punkten. Daraufhin wird das Dialogfeld **delegatearguments** angezeigt, in dem Sie diese Eigenschaft festlegen können. Klicken Sie auf das Feld **Argument erstellen** , um die Argumente hinzuzufügen.|

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Definieren und Verarbeiten von Aktivitätsdelegaten im Workflow-Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)