---
title: 'Vorgehensweise: Erstellen von Konsolen Anwendungen für sequenzielle Workflows (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662725"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Vorgehensweise: Erstellen von Konsolenanwendungen für sequenzielle Workflows (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine Konsolenanwendung für sequenzielle Workflows mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] zu erstellen, die von [!INCLUDE[vs2010](../includes/vs2010-md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

### <a name="to-create-a-sequential-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für sequenzielle Workflows

1. Starten Sie Visual Studio.

2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. Wählen Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** aus, um auf den Legacy-Designer zuzugreifen.

    > [!NOTE]
    > Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.

4. Wählen Sie im Bereich **Projekttypen** die Option Visual c#-Projekte oder Visual Basic Projekte (unter **andere Sprachen**) aus, und wählen Sie dann **Workflow**aus.

5. Wählen Sie im Bereich **Vorlagen** die Option **Konsolenanwendung für sequenzielle Workflows**aus.

6. Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, damit es leicht zu erkennen ist.

7. Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem Sie das Projekt speichern möchten, oder klicken Sie auf **Durchsuchen** , um zu diesem Verzeichnis zu navigieren.

     Der Windows Forms-Designer wird geöffnet und zeigt Form1 des neu erstellten Projekts an.

8. Klicken Sie auf **OK**.

     Der Workflow-Designer wird geöffnet und zeigt die Workflowentwurfsoberfläche des neu erstellten sequenziellen Workflows an.

9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfs Oberfläche im Bereich **Drop Activity** festgelegt.

## <a name="see-also"></a>Weitere Informationen
 [Erstellen von Legacy Workflow Projekten](../workflow-designer/creating-legacy-workflow-projects.md) [entwickeln von Workflows](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)