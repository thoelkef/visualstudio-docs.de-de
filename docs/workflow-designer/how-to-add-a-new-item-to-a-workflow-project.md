---
title: 'Workflow-Designer: ein neues Element zum Workflow Projekt hinzufügen'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cdea5b3cbf99ab8213c320acc82665816062dca
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189638"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Gewusst wie: Hinzufügen eines neuen Elements zu einem Workflow Projekt

Nachdem Sie ein Workflow Projekt erstellt haben, können Sie dem Projekt Workflow Aktivitäten, Designer und andere vertraute Visual Studio-Elemente hinzufügen.

In der folgenden Tabelle sind die Windows Workflow Foundation (WF)-Elemente aufgelistet, die Sie einem Workflow Projekt hinzufügen können:

| -Name | Beschreibung |
|-| - |
| Aktivität | Eine Aktivität, die aus anderen Aktivitäten besteht. Wenn Sie dieses Element auswählen, wird dem Projekt die gleiche XAML-Datei hinzugefügt wie beim Auswählen der Vorlage **Aktivitäts Bibliothek** für ein neues Projekt. Weitere Informationen zu diesem Verfahren finden Sie unter [Erstellen eines Workflow Projekts](creating-a-workflow-project.md). |
| Aktivitätsdesigner | Ein Designer, mit dem die Behandlung einer Aktivität zur Entwurfszeit angepasst wird. Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **Aktivitäts Designer Bibliothek** für ein neues Projekt. |
| Codeaktivität | Eine Aktivität mit in Code geschriebener Ausführungslogik. Eine Quellcodedatei mit einer Überschreibung der <xref:System.Activities.CodeActivity.Execute%2A>-Methode wird bereits für Sie generiert. |
| WCF-Workflowdienst | Ein [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Dienst, der mithilfe von Workflowaktivitäten erstellt wurde. Durch die Auswahl dieses Elements werden dem Projekt die gleichen Dateien hinzugefügt wie beim Auswählen der Vorlage **WCF-Workflow Dienst Anwendung** für ein neues Projekt. Weitere Informationen zu diesem Verfahren finden Sie unter Gewusst [wie: Erstellen einer WCF-Workflow Dienst Anwendung](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>So fügen Sie ein neues Element zu einem Workflowprojekt hinzu

1. Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Wählen Sie im linken Bereich die Kategorie **Workflow** aus, und wählen Sie dann eine Workflow Element Vorlage aus.

   > [!NOTE]
   > Wenn die Kategorie **Workflow** nicht angezeigt wird, installieren Sie zunächst die **Windows Workflow Foundation** Komponente von Visual Studio. Ausführliche Anweisungen finden Sie unter [install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Geben Sie unten im Dialogfeld im Feld **Name** einen Namen für das Element ein.

1. Wählen Sie **Hinzufügen** aus, um das Element dem Projekt hinzuzufügen.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Workflow Projekts](../workflow-designer/creating-a-workflow-project.md)