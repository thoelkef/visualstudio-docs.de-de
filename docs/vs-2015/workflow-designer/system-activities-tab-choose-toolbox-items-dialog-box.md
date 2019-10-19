---
title: Registerkarte "System. Activities", Dialog Feld "Toolbox Elemente auswählen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655169"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities (Registerkarte), Toolboxelemente auswählen (Dialogfeld)
Auf dieser Registerkarte des Dialog Felds **Toolbox Elemente auswählen** wird eine Liste mit [!INCLUDE[wf](../includes/wf-md.md)] Aktivitäten, Vorlagen und Elementen angezeigt, die Ihnen zur Verfügung stehen. Um diese Liste anzuzeigen, wählen Sie **im Menü Extras die Option** **Toolbox Elemente** auswählen aus, oder klicken Sie mit der rechten Maustaste auf die **Toolbox** , und **Wählen Sie Elemente auswählen** aus, um das Dialogfeld **Toolbox Elemente auswählen** anzuzeigen, und wählen Sie **dann Registerkarte System. Activities** . Standardmäßig enthält die Liste Workflow Aktivitäten aus den Assemblys System. Activities, System. Service Model. Activities und System. Activities. Core. Presentation. Allerdings werden nur die vom System bereitgestellten Aktivitäten und Aktivitäten, die über andere in der **Toolbox** angezeigte Assemblys hinzugefügt wurden, standardmäßig aktiviert. Zuletzt hinzugefügte Aktivitäten werden automatisch aktiviert und in der **Toolbox** angezeigt, wenn Sie im Dialogfeld auf **OK** klicken. Außerdem werden diese Elemente in der **Toolbox** unter einer neuen Kategorie angezeigt, die dem Namespace entspricht, in dem sich die Aktivität/das Element/die Vorlage befindet.

> [!WARNING]
> Wenn Sie versuchen, eine Assembly hinzuzufügen, die keine Workflowaktivitäten enthält, wird ein Dialogfeld mit einer Fehlermeldung angezeigt, die besagt, dass die Assembly keine Aktivitäten enthält.

 Dieses Dialogfeld ist Projekt agnostisch, sodass die Registerkarte **System. Activities** weiterhin in einem eigenständigen XAML-oder einem nicht-Workflow-Projekttyp angezeigt wird.

 Die Filterung erfolgt auf jeder Registerkarte. Dies bedeutet, dass es nicht möglich ist, Workflow Aktivitäten über die Registerkarte **.NET-Komponente** hinzuzufügen. Sie müssen über die Registerkarte **System. Activities** hinzugefügt werden.

 Sie können alle Elemente, die nicht in der **Toolbox** angezeigt werden sollen, auf dieser Dialogfeld Registerkarte deaktivieren. Alternativ dazu können Sie auch die Option "Kontextmenü **Löschen** " in der **Toolbox** verwenden. Wenn Sie auf eine Assembly verweisen, wird das Element nicht aus dem  **Toolbox**.

 Durch Ziehen und Ablegen im Designer wird die Aktivität instanziiert und die Assembly, die das Element enthält, automatisch der Liste von Assemblys hinzugefügt, auf die verwiesen wird. Außerdem gilt, wenn die Aktivität auf eine Assembly C verweist, wird C nicht der Liste von Assemblys, auf die verwiesen wird, hinzugefügt. Die Assembly C muss sich im GAC oder im selben Verzeichnis wie die Aktivität B befinden. Im eigenständigen Fall muss sich die Assembly im GAC oder in den Überprüfungs Pfaden von vs befinden. Nur dann können Sie die Aktivität auf die Workflow-Designer-Oberfläche ziehen und dort ablegen.

 **Toolbox** Einstellungen werden standardmäßig als Benutzeroptionen gespeichert. Wenn Sie die **Toolbox**zum nächsten Mal öffnen, wird Ihre angepasste Liste mit Workflow Aktivitäten angezeigt. Ein Nebeneffekt besteht darin, dass Sie, wenn Sie Ihre spezifischen Domänen Elemente der **Toolbox** über das Dialogfeld **Toolbox Elemente auswählen** hinzugefügt haben, diese Elemente weiterhin anzeigen, wenn Sie auch in einer Workflow Konsolenanwendung arbeiten. Wenn Sie Sie nicht anzeigen möchten, löschen Sie Sie mithilfe des Kontextmenüs, oder deaktivieren Sie Sie wie zuvor im Dialogfeld **Toolbox Elemente auswählen** .

 Die Spalten in diesem Dialogfeld enthalten die folgenden Informationen:

 Name listet die Namen der Workflow Aktivitäten auf, die derzeit auf dem lokalen Computer registriert sind.

 Namespace zeigt die Hierarchie des .NET Framework Klassenbibliothek-Namespace an, der die Struktur der Aktivität definiert.

 AssemblyName zeigt den Namen und die Version der .NET Framework Assembly an, die die Aktivität enthält.

 Verzeichnis zeigt den Speicherort der .NET Framework Assembly an, in der die Workflow Aktivitäten enthalten sind. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache.

 Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.