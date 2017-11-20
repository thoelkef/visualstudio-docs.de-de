---
title: "Richtlinien für das Importieren von Wiederverwendbaren Workflows | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32e0180f804a8b35946a4d7a4d02f72dd6deb7d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Richtlinien für das Importieren von wiederverwendbaren Workflows
  Verwenden Sie zum Importieren von wiederverwendbaren Workflows, die im SharePoint-Designer erstellt, die die Projektvorlage "Wiederverwendbaren SharePoint 2010-Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Diese Vorlage importiert eine *deklarative* *Workflow* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-nur) und konvertiert ihn in ein *code Workflow*, also in einem Workflow, die Sie entweder mit verbessern können [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] Code. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Exemplarische Vorgehensweise: Importieren ein Wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Das Importieren von Wiederverwendbaren SharePoint 2010-Workflow-Vorlage kann jedoch nur für farmlösungen importiert werden. Wenn Sie den Workflow als sandkastenlösung bereitstellen möchten, importieren Sie sie mithilfe der Vorlage für SharePoint 2010-Lösungspaket importieren. Allerdings durch dieses Vorgehen kann nicht konvertiert werden, um code von Workflows und werden nicht als solche zu ändern.  
  
## <a name="importing-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importieren von Wiederverwendbaren Workflows mithilfe der Vorlage der Import Wiederverwendbaren Workflows  
 Mithilfe der Vorlage Wiederverwendbaren SharePoint 2010-Workflow importieren ein wiederverwendbares Workflows importieren, können Sie ausführen oder ändern Sie die Projektmappe genau wie alle anderen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Lösung, aber Sie müssen möglicherweise einige Elemente manuell korrigieren.  
  
### <a name="importing-task-forms"></a>Importieren von Taskformularen  
 Die Projektvorlage Wiederverwendbaren SharePoint 2010-Workflow importieren importiert alle Initiierung und Zuordnung Formulare, aber nur ein Aufgabenformular importiert, da der Code-Workflow-Schema nur ein Aufgabenformular erlaubt. Alle zusätzlichen taskformularen aus der ursprünglichen Workflowprojektmappe abgelegt werden die **andere importierte Dateien** Ordner **Projektmappen-Explorer**.  
  
## <a name="importing-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importieren von Wiederverwendbaren Workflows mithilfe der Import SharePoint 2010-Lösung Paketvorlage  
 Wenn Sie ein wieder verwendbaren Workflows mithilfe der SharePoint 2010-Lösungspaket importieren-Vorlage importieren, müssen Sie Folgendes berücksichtigen:  
  
-   Nach dem Importieren des Workflows an, Sie können sofort bereitstellen und führen Sie es in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] durch Auswählen der F5-Taste. Wenn Sie alle Elemente in der Workflow in importierten Projektmappen ändern, möglicherweise Sie Elemente im Projekt manuell korrigieren, vor der Bereitstellung und der Workflow ausgeführt werden können.  
  
-   Da der Workflow deklarative ist, kann Code darauf hinzugefügt werden. Um den Workflow in einem Code-Workflow zu konvertieren, müssen Sie ihn in importieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der Vorlage Wiederverwendbaren SharePoint 2010-Workflow importieren.  
  
-   Während Sie die Workflow-Designer (.xoml)-Datei in der Entwurfsansicht bearbeiten können, wird empfohlen, dass Sie diese in der Quellansicht bearbeiten, da die Workflow-Designer "false" Fehler angezeigt.  
  
-   Im Workflow-Debuggen funktioniert nicht für deklarative Inhalt. Haltepunkte in der [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] werden nicht erreicht.  
  
## <a name="importing-globally-reusable-workflow-solutions"></a>Importieren von Global verwendbare-Workflow-Projektmappen  
 Global wiederverwendbare Workflows können nicht importiert werden, mithilfe der Vorlage importieren Wiederverwendbaren SharePoint 2010-Workflow. Um einen global wiederverwendbaren Workflow importieren, müssen Sie sie in einer nicht global wieder verwendbaren Workflows zu konvertieren, oder müssen Sie die SharePoint 2010-Lösungspaket importieren Vorlage verwenden.  
  
 Um den Workflow zu konvertieren, erstellen Sie eine Kopie des Global wieder verwendbaren Workflows im SharePoint-Designer (durch Öffnen das Kontextmenü für den Workflow, und drücken Sie dann die **als Kopie speichern**). Importieren Sie mit der Vorlage Wiederverwendbaren SharePoint 2010-Workflow importieren, in der neuen wieder verwendbaren Workflows [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Um global wiederverwendbaren Workflow importieren, ohne diese zu ändern, verwenden Sie SharePoint 2010-Lösungspaket importieren Sie die Vorlage ein. Wenn Sie diese Methode verwenden, wird der Workflow wird nicht zu einem Workflow Code konvertiert und bleibt ein deklarativer Workflow.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  