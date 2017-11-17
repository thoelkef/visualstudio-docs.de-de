---
title: "Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: "12"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a61c8f4ea5e9d9cc6d4ab13437d2ec4d4eef7ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-an-activity-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren. Die Vorlage Aktivitätsbibliothek in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] erstellen können.  
  
### <a name="to-create-a-workflow-activity-library"></a>So erstellen Sie eine Workflowaktivitätsbibliothek  
  
1.  Starten Sie [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt...** .  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In der **Projekttypen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** Projekte oder **Visual Basic** Gruppierungen je nach Ihrer Bevorzugte Sprache.  
  
4.  In der **Vorlagen** klicken Sie im Bereich **Aktivitätsbibliothek**.  
  
5.  In der **Namen** Feld geben einen beschreibenden Namen für das Projekt, um es einfach identifizieren zu können.  
  
6.  In der **Speicherort** den Suchbegriff in das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** navigieren.  
  
7.  In der **Lösung** Feld, geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie auf **OK**.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], klicken Sie mit der mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt...**  So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML-Format. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] wird geöffnet und zeigt den Zeichenbereich für die benutzerdefinierte Aktivität an.  
  
9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche, um sie in die benutzerdefinierte Aktivität aufzunehmen.  
  
    > [!CAUTION]
    >  Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>-Aktivität oder <xref:System.Activities.Statements.Flowchart>-Aktivität.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen Sie eine Aktivität](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)