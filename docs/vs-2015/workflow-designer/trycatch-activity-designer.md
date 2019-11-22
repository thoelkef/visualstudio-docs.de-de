---
title: Trycatch-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654660"
---
# <a name="trycatch-activity-designer"></a>TryCatch-Aktivitätsdesigner
Der **trycatch** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.TryCatch>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-trycatch-activity"></a>Die TryCatch-Aktivität
 Die <xref:System.Activities.Statements.TryCatch>-Aktivität enthält eine <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität, eine Auflistung von **catch \<TException >** und eine <xref:System.Activities.Statements.TryCatch.Finally%2A>-Aktivität. Eine <xref:System.Activities.Statements.Catch%601> vom Typ **TException** enthält eine <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> und eine <xref:System.Activities.Statements.Catch%601.Action%2A>. Zusammen werden diese verwendet, um einen typischen ausnahmebasierten Fehlerbehandlungsmechanismus zu implementieren. Eine <xref:System.Activities.Statements.TryCatch>-Aktivität versucht, die zugehörige <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität auszuführen. Wenn die <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität eine Ausnahme auslöst, verwendet die <xref:System.Activities.Statements.TryCatch> Aktivität die **catch < TException-\>** Auflistung, um die Ausnahme abzugleichen. Wenn eine Übereinstimmung vorliegt, wird die <xref:System.Activities.Statements.Catch%601.Action%2A> der entsprechenden **catch-\<TException >** ausgeführt und dient als Fehler Behandlungs Logik für die Ausnahme. Wenn die Aktivitäten im Abschnitt <xref:System.Activities.Statements.TryCatch.Try%2A> erfolgreich abgeschlossen werden oder die Aktivitäten in <xref:System.Activities.Statements.TryCatch.Catches%2A> erfolgreich abgeschlossen werden, führt die <xref:System.Activities.Statements.TryCatch>-Aktivität die zugehörige <xref:System.Activities.Statements.TryCatch.Finally%2A>-Aktivität aus. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Ausnahmen](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Verwenden des TryCatch-Aktivitätsdesigners
 Der **trycatch** -Aktivitäts Designer befindet sich in der Kategorie **Fehlerbehandlung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken. (Sie können auch **Symbolleiste** **im Menü Ansicht** oder CTLR + ALT + X.)

 Der **trycatch** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Hierdurch erstellen Sie eine <xref:System.Activities.Statements.TryCatch>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert TryCatch. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **trycatch** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden. Die anderen Eigenschaften müssen auf der Oberfläche des **trycatch** -Aktivitäts Designers bearbeitet werden.

 Klicken Sie in der rechten oberen Ecke des **trycatch** -Designers auf die Schaltfläche erweitern, um die Felder **ausprobieren**, **fängt**und **schließlich** in der erweiterten Ansicht anzuzeigen. Um einen catch hinzuzufügen, klicken Sie auf die Schaltfläche **neuen Catch hinzufügen** im **trycatch** -Designer. Die Schaltfläche nimmt die Form eines Kombinationsfelds an. Wählen Sie einen Ausnahmetyp aus, und drücken Sie die EINGABETASTE, um den Catch hinzuzufügen. Nach dem Hinzufügen eines **catch**-Blocks wird der catch-Bereich erweitert, und eine Aktivität kann im catch abgelegt werden, um die Ausführungs Logik für den catch zu definieren. Auf der rechten Seite des erweiterten Catch-Bereichs befindet sich ein Textfeld. In dieses Textfeld können Sie den Namen einer Ausnahmevariablen eingeben. Die Exception-Variable kann nur für Aktivitäten innerhalb desselben **catch**verwendet werden.

 Der **trycatch** -Designer unterstützt das Bearbeiten von **catch**nicht. Wenn Sie den Ausnahmetyp ändern möchten, müssen Sie den **catch** löschen und einen neuen hinzufügen. Ein **catch** kann gelöscht werden, indem Sie ihn auswählen und löschen oder indem Sie das Menü **Löschen** im Kontextmenü verwenden, auf das Sie mit der rechten Maustaste klicken.

### <a name="the-trycatch-properties"></a>Die TryCatch-Eigenschaften
 Die folgende Tabelle zeigt die <xref:System.Activities.Statements.TryCatch>properties und beschreibt, wie Sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.TryCatch>-Aktivität an. Der Standardwert ist TryCatch.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Die Aktivität wird erstmalig ausgeführt wird, wenn <xref:System.Activities.Statements.TryCatch> ausgeführt wird.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Die Auflistung der **catch** -Elemente, die geprüft werden soll, wenn die <xref:System.Activities.Statements.TryCatch.Try%2A>-Aktivität eine Ausnahme auslöst.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Die Aktivität, die ausgeführt werden soll, wenn die Ausführung von <xref:System.Activities.Statements.TryCatch.Try%2A> und aller erforderlichen Aktivitäten in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung abgeschlossen wurde.<br /><br /> Sie müssen mindestens eine Aktivität in der <xref:System.Activities.Statements.TryCatch.Catches%2A>-Auflistung oder eine Aktivität im <xref:System.Activities.Statements.TryCatch.Finally%2A>-Block hinzufügen.|

## <a name="see-also"></a>Siehe auch
 [Sammlung](../workflow-designer/collection-activity-designers.md) [Erneut auslösen](../workflow-designer/rethrow-activity-designer.md) [Auslösen](../workflow-designer/throw-activity-designer.md)