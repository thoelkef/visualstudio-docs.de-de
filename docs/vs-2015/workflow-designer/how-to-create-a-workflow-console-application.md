---
title: 'Vorgehensweise: Erstellen Sie eine Workflowkonsolenanwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 285c19e7814c369866fe70fa6f13e48efb6da359
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957901"
---
# <a name="how-to-create-a-workflow-console-application"></a>Vorgehensweise: Erstellen einer Konsolenanwendung für Workflows
Mit [!INCLUDE[wf](../includes/wf-md.md)] können Sie Workflows zum Ausführen von Systemprozessen oder menschlichen Prozessen erstellen. Der [!INCLUDE[wfd1](../includes/wfd1-md.md)] stellt die Entwurfsoberfläche zum Erstellen dieser Workflows bereit. Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] kann verwendet werden, um Workflows in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu erstellen, oder er kann in andere Anwendungen integriert werden, die den Designer neu hosten.  
  
 In diesem Thema wird beschrieben, wie der [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] verwendet wird, um einen Workflow in einer Konsolenanwendung zu erstellen.  
  
### <a name="to-create-a-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für Workflows  
  
1.  Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Auf der **Datei** Startmenü **neu**, und wählen Sie dann **Projekt...** .  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In der **installierte Vorlagen** wählen Sie im Bereich **Workflow** entweder die **Visual C#-** oder **Visual Basic** Gruppierungen, je nach Ihrer von Ihnen bevorzugte Sprache.  
  
4.  Wählen Sie im mittleren Bereich **Konsolenanwendung für Workflows**.  
  
5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** dorthin navigieren.  
  
7.  In der **Lösung** Geben Sie den Namen für die neue Projektmappe. Klicken Sie auf **OK** zum Erstellen der Anwendung.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt...** zum Öffnen der **neues Projekt** Dialogfeld. Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Workflowdefinition in XAML, und die Konsolenanwendungsdefinition ist in Quellcode. Der [!INCLUDE[wfd2](../includes/wfd2-md.md)] wird geöffnet und zeigt den Canvas für den Workflow an, den Sie erstellt haben.  
  
9. Um einen Workflow zu verfassen, ziehen Sie die Aktivitäten oder andere Workflowelemente von der **Toolbox** auf die Entwurfsoberfläche des Workflows.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)