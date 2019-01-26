---
title: Richtlinien für das Importieren von Wiederverwendbaren Workflows | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 329d38e8c258148830347a506ceef5845c1cf268
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874275"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Richtlinien für das Importieren von wiederverwendbaren workflows
  Verwenden Sie zum Importieren von wiederverwendbaren Workflows in SharePoint Designer erstellte die Projektvorlage "Wiederverwendbaren SharePoint 2010-Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Diese Vorlage importiert eine *deklarative* *Workflow* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-nur) und konvertiert ihn in eine *code Workflow*, dies ist ein Workflow, der entweder mit der Sie verbessern können [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] Code. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Exemplarische Vorgehensweise: Importieren ein wiederverwendbares Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Allerdings kann die Vorlage importieren von Wiederverwendbaren SharePoint 2010-Workflow nur farmlösungen importieren. Wenn Sie den Workflow als sandkastenlösung bereitstellen möchten, importieren Sie sie mit der Vorlage für die SharePoint 2010-Lösungspaket importieren. Hingegen auf diese Weise kann nicht konvertiert werden, um die Workflow-code und ist nicht möglich, daher ändern.  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importieren von wiederverwendbaren Workflows mithilfe der Vorlage Wiederverwendbaren Workflow importieren
 Wenn Sie einen wiederverwendbaren Workflow importieren, mit der Vorlage Wiederverwendbaren SharePoint 2010-Workflow importieren, können Sie ausführen oder ändern Sie die Lösung wie jede andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Lösung, aber Sie müssen möglicherweise einige Elemente manuell zu beheben.  
  
### <a name="import-task-forms"></a>Importieren von taskformularen
 Die Projektvorlage Wiederverwendbaren SharePoint 2010-Workflow importieren importiert alle Initiierung und Zuordnung Formulare, jedoch nur jeweils ein Task-Format importiert, da der Code-Workflow-Schema nur ein Aufgabenformular erlaubt. Alle weiteren Aufgabenformulare aus der ursprünglichen Workflowprojektmappe abgelegt werden die **andere importierte Dateien** Ordner **Projektmappen-Explorer**.  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importieren von wiederverwendbaren Workflows mithilfe der Vorlage für die SharePoint 2010-Lösungspaket importieren
 Wenn Sie einen wiederverwendbaren Workflow importieren, mit der Vorlage für die SharePoint 2010-Lösungspaket importieren, müssen Sie Folgendes berücksichtigen:  
  
-   Nach dem Importieren des Workflows können Sie sofort bereitstellen und ausführen können [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] durch Auswählen der **F5** Schlüssel. Wenn Sie alle Elemente in der Workflow in der importierten Lösung ändern, möglicherweise Sie jedoch Elemente in das Projekt manuell korrigieren, vor der Bereitstellung und der Workflow ausgeführt werden können.  
  
-   Da Workflows deklarativ ist, kann der Code darauf hinzugefügt werden. Um den Workflow in einem Code-Workflow zu konvertieren, müssen Sie ihn in importieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der Vorlage importieren von Wiederverwendbaren SharePoint 2010-Workflow.  
  
-   Während Sie die Workflow-Designer (.xoml)-Datei, in der Entwurfsansicht bearbeiten können, wird empfohlen, dass Sie es in der Quellansicht bearbeiten, da der Workflow-Designer falsche Fehler angezeigt.  
  
-   Im Workflow-Debuggen funktioniert nicht für deklarative Inhalt. Haltepunkte in der [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] werden nicht erreicht.  
  
## <a name="import-globally-reusable-workflow-solutions"></a>Importieren Sie Global wieder verwendbaren Workflow-Projektmappen
 Global wiederverwendbare Workflows können nicht importiert werden, mithilfe der Vorlage Wiederverwendbaren SharePoint 2010 Workflow importieren. Um einen global wiederverwendbaren Workflow importieren, müssen Sie ihn in einen nicht global wieder verwendbaren Workflow konvertieren, oder müssen Sie mit der Vorlage für die SharePoint 2010-Lösungspaket importieren.  
  
 Um den Workflow zu konvertieren, stellen Sie eine Kopie des Global wiederverwendbare Workflows in SharePoint Designer (öffnen das Kontextmenü für den Workflow, und wählen Sie dann **als Kopie speichern**). Klicken Sie dann importieren Sie die neuen wiederverwendbaren Workflow mit der Vorlage "Wiederverwendbaren SharePoint 2010-Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Um die Global wiederverwendbaren Workflow importieren, ohne es zu ändern, verwenden Sie die SharePoint 2010-Lösungspaket importieren-Vorlage. Wenn Sie diese Methode verwenden, wird der Workflow wird nicht zu einem Code-Workflow konvertiert, und ein deklarativer Workflow bleibt.  
  
## <a name="see-also"></a>Siehe auch
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
