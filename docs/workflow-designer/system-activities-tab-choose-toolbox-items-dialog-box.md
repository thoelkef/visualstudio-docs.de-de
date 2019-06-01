---
title: 'Workflow-Designer: System.Activities, Toolboxelemente auswählen'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e057a0ff61bd095dd011c85970fd23ab1da75838
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432055"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities (Registerkarte), Toolboxelemente auswählen (Dialogfeld)

Auf dieser Registerkarte des der **Toolboxelemente** Dialogfeld zeigt eine Liste der Windows Workflow Foundation (WF)-Aktivitäten, Vorlagen und verfügbaren Elemente für Sie. Um diese Liste anzuzeigen, wählen **Toolboxelemente auswählen** aus der **Tools** Menü oder durch Rechtsklick auf die **Toolbox** , und wählen **Elemente auswählen**zum Anzeigen der **Toolboxelemente auswählen** (Dialogfeld), und wählen Sie dann die **System.Activities** Registerkarte. Standardmäßig enthält die Liste Workflowaktivitäten aus den Assemblys System.Activities, System.ServiceModel.Activities und System.Activities.Core.Presentation; allerdings nur die vom System bereitgestellten Aktivitäten und Aktivitäten hinzugefügt, die durch andere Assemblys angezeigt, der **Toolbox** sind standardmäßig aktiviert. Vor kurzem hinzugefügt Aktivitäten werden automatisch markiert und werden in der **Toolbox** beim Klicken auf **OK** im Dialogfeld. Darüber hinaus diese Elemente werden in der **Toolbox** in einer neuen Kategorie, die dem Namespace entspricht, auf dem die Aktivität/Element/die Vorlage gespeichert.

> [!WARNING]
> Wenn Sie versuchen, eine Assembly hinzuzufügen, die keine Workflowaktivitäten enthält, wird ein Dialogfeld mit einer Fehlermeldung angezeigt, die besagt, dass die Assembly keine Aktivitäten enthält.

 Dieses Dialogfeld ist Projekt bezogen und somit die **System.Activities** Registerkarte wird weiterhin in eigenständigen XAML oder einen nicht-Workflow-Projekttyp angezeigt.

 Die Filterung wird auf jeder Registerkarte ausgeführt. Dies bedeutet, es ist nicht möglich, zum Hinzufügen von Workflowaktivitäten, durch die **.NET Component** Registerkarte. Sie müssen über hinzugefügt werden die **System.Activities** Registerkarte selbst.

 Deaktivieren Sie alle Elemente, die Sie nicht in finden Sie unter möchten den **Toolbox** in diesem Dialogfeld Tab oder alternativ Sie können dazu die **löschen** Option in der Maustaste der **Toolbox**und Aufheben des Verweises auf eine Assembly entfernt sich nicht auf das Element aus der **Toolbox**.

 Durch Ziehen und Ablegen im Designer wird die Aktivität instanziiert und die Assembly, die das Element enthält, automatisch der Liste von Assemblys hinzugefügt, auf die verwiesen wird. Außerdem gilt, wenn die Aktivität auf eine Assembly C verweist, wird C nicht der Liste von Assemblys, auf die verwiesen wird, hinzugefügt. Assembly C muss im GAC oder dem gleichen Verzeichnis wie Aktivität b Im Fall eines eigenständigen muss die Assembly im GAC oder den überprüfungspfaden von VS zu sein. Nur dann können Sie die Aktivität auf die Workflow-Designer-Oberfläche ziehen und dort ablegen.

 **Toolbox** Einstellungen werden standardmäßig als Benutzeroptionen gespeichert daher beim nächsten Öffnen, wenn die **Toolbox**, die benutzerdefinierte Liste von Workflowaktivitäten angezeigt. Ein Nebeneffekt dieser ist, die, wenn Sie bestimmte Elemente Ihrer Domäne, hinzugefügt haben die **Toolbox** über die **Toolboxelemente auswählen** Dialogfeld Sie weiterhin diese Elemente finden bei der Arbeit einer Konsolenanwendung für Workflows ebenfalls. Wenn Sie nicht, um sie anzuzeigen möchten, klicken Sie dann löschen Sie sie mit der rechten Maustaste, oder deaktivieren Sie diese über die **Toolboxelemente** Dialogfeld wie bereits erwähnt.

 Die Spalten in diesem Dialogfeld enthalten die folgenden Informationen:

 Name

 Führt die Namen der Workflowaktivitäten auf, die aktuell auf dem lokalen Computer registriert sind.

 Namespace

 Zeigt die Hierarchie der Namespaces der .NET Framework-Klassenbibliothek an, welche die Struktur der Aktivität definiert.

 Assemblyname

 Zeigt den Namen und die Version der .NET Framework-Assembly an, die die Aktivität enthält.

 Verzeichnis

 Zeigt den Speicherort der .NET Framework-Assembly an, die die Workflowaktivitäten enthält. Der Standardspeicherort für alle Assemblys ist der globale Assemblycache.

 Klicken Sie zum Sortieren der aufgeführten Komponenten auf eine beliebige Spaltenüberschrift.