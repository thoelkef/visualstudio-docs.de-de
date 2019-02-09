---
title: Workflow-Designer - WriteLine-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dd6e3c617749d82533d8bccb7f0caaa073ac26
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930323"
---
# <a name="writeline-activity-designer"></a>WriteLine-Aktivitätsdesigner

Die **WriteLine** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.WriteLine> Aktivität.

## <a name="the-writeline-activity"></a>Die WriteLine-Aktivität

Die <xref:System.Activities.Statements.WriteLine>-Aktivität schreibt Text in ein angegebenes <xref:System.IO.TextWriter>-Objekt. Wenn kein <xref:System.IO.TextWriter> angegeben wird, schreibt <xref:System.Activities.Statements.WriteLine> den Text in die Konsole.

### <a name="using-the-writeline-activity-designer"></a>Verwenden des WriteLine-Aktivitätsdesigners

Zugriff die **WriteLine** Aktivitäts-Designer in der **primitive** Kategorie der **Toolbox**. Die **WriteLine** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.WriteLine>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert WriteLine erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **WriteLine** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-writeline-properties"></a>Die WriteLine-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.WriteLine>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster bearbeitet werden, und einige davon können auf die Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.WriteLine>-Aktivität. Der Standardwert lautet WriteLine. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Der zu schreibende Text. Um die Eigenschaft festzulegen, geben Sie einen Visual Basic-Ausdruck in der **Text** Feld der **WriteLine** -Aktivitätsdesigner oder im Eigenschaftenraster.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Die <xref:System.IO.TextWriter>-Instanz, an die die <xref:System.Activities.Statements.WriteLine>-Aktivität den <xref:System.Activities.Statements.WriteLine.Text%2A>-Text ausgibt. Der Standardwert ist die Konsole.|

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)