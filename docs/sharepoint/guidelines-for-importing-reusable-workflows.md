---
title: "Richtlinien f&#252;r das Importieren von wiederverwendbaren Workflows"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Importieren von Elementen [SharePoint-Entwicklung in Visual Studio]"
  - "Wiederverwendbare Workflows [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Importieren von Elementen"
  - "SharePoint-Entwicklung in Visual Studio, Wiederverwendbare Workflows"
ms.assetid: 851043dd-ecbe-49ab-b5b7-5ea7b699df12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Richtlinien f&#252;r das Importieren von wiederverwendbaren Workflows
  Um wiederverwendbare Workflows zu importieren in SharePoint Designer erstellte, verwenden die 2010\-Workflowprojektvorlage Wiederverwendbaren SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Diese Vorlage importiert einen *deklarativen* *Workflow* \(nur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\) und konvertiert ihn in einen *Codeworkflow*, den Sie mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\- oder [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]\-Code erweitern und verbessern können.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 kann jedoch Wiederverwendbaren SharePoint 2010\-Workflowvorlage nur aus Farmlösungen importieren.  Wenn Sie den Workflow als Sandkastenlösung bereitstellen möchten, importieren Sie ihn mit der Import\-SharePoint2010\-Lösungspaketvorlage.  jedoch auf diese Weise können Sie diese nicht in Codeworkflows konvertieren und werden nicht in der Lage sein, diese als solcher zu ändern.  
  
## Importieren wiederverwendbarer Workflows mit der Vorlage Wiederverwendbaren Workflow importieren  
 Wenn Sie einen wiederverwendbaren Workflow importieren, indem Sie die Vorlage 2010\-Workflowvorlage SharePoint verwenden, können Sie die Projektmappe wie jede andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \- SharePoint\-Lösung ausführen oder ändern, aber Sie müssen möglicherweise einige Elemente manuell korrigieren.  
  
### Importieren von Aufgabenformularen  
 Die Vorlage Wiederverwendbaren SharePoint 2010\-Workflowprojektvorlage importiert alle Initiierungs\- und Zuordnungsformulare jedoch nur ein Aufgabenformular importiert, da das Codeworkflowschema nur ein Aufgabenformular.  Alle eventuellen weiteren Aufgabenformulare aus der ursprünglichen Workflowprojektmappe werden im Ordner **Andere importierte Dateien** im **Projektmappen\-Explorer** gespeichert.  
  
## Importieren wiederverwendbarer Workflows mit der Import\-SharePoint2010\-Lösungspaket\-Vorlage importieren  
 Wenn Sie einen wiederverwendbaren Workflow importieren, indem Sie die Import\-SharePoint2010\-Lösungspaketvorlage verwenden, müssen Sie die folgenden Punkte berücksichtigen:  
  
-   Nachdem Sie den Workflow importiert haben, können Sie ihn sofort bereitstellen und in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ausführen, indem Sie die F5\-TASTE auswählen.  Wenn Sie jedoch in der importierten Projektmappe Änderungen am Workflow vornehmen, müssen Sie ggf. einige Elemente im Projekt manuell korrigieren, bevor Sie den Workflow bereitstellen und ausführen können.  
  
-   Da der Workflow deklarativ ist, kann kein Code hinzugefügt werden.  Um den Workflow in einen Codeworkflow zu konvertieren, müssen Sie ihn in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren indem Sie die Vorlage 2010\-Workflowvorlage SharePoint verwenden.  
  
-   Obwohl Sie die XOML\-Datei für den Workflow\-Designer in der Entwurfsansicht bearbeiten können, wird empfohlen, diese Datei in der Quellansicht zu bearbeiten, da der Workflow\-Designer falsche Fehler anzeigt.  
  
-   Das Debuggen deklarativer Inhalte im Workflow ist nicht möglich.  Im [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] definierte Haltepunkte werden nicht berücksichtigt.  
  
## Importieren von global wiederverwendbaren Workflowprojektmappen  
 Global wiederverwendbare Workflows können nicht importiert werden, indem die 2010\-Workflowvorlage Wiederverwendbaren SharePoint verwendet.  Um einen global wiederverwendbaren Workflow zu importieren, müssen Sie ihn in einen nicht global wiederverwendbaren Workflow konvertieren oder die Import\-SharePoint2010\-Lösungspaketvorlage verwenden.  
  
 Um den Workflow konvertieren, erstellen Sie eine Kopie des global wiederverwendbaren Workflows im SharePoint\-Designer \(durch das Öffnen des Kontextmenüs für den Workflow und anschließend **Als Kopie speichern** auswählen\).  Importieren Sie dann den neuen wiederverwendbaren Workflow mit der 2010\-Workflowvorlage Wiederverwendbaren SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Um den global wiederverwendbaren Workflow ohne sie zu ändern zu importieren, verwenden Sie die Import\-SharePoint2010\-Lösungspaketvorlage.  Wenn Sie diese Methode verwenden, ist der Workflow nicht in einen Codeworkflow konvertiert und bleibt deklarativ.  
  
## Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
  
  