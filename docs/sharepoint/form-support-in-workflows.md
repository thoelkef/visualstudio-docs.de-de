---
title: "Unterst&#252;tung von Formularen in Workflows | Microsoft Docs"
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
  - "SharePoint-Entwicklung in Visual Studio, Workflows"
  - "Workflows [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Unterst&#252;tung von Formularen in Workflows
  Vier Typen von Formularen können in einem Workflow verwendet werden: Zuordnung, Initiierung, Aufgabe und Änderung.  Diese Formulartypen können entweder auf einem ASPX\-Formular oder einem InfoPath\-Formular basieren.  Die Unterstützungsebene, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] für ein bestimmtes Formular bereitstellt, hängt von mehreren Faktoren ab, die in den folgenden Tabellen beschrieben werden.  Weitere Informationen zu Workflowformulartypen, finden Sie unter [Workflow bildet Übersicht](http://go.microsoft.com/fwlink/?LinkId=185228) auf der MSDN\-Website.  
  
## XML\-Umgestaltung  
 Wenn Sie ein ASPX\-Zuordnungs\- oder \-Initiierungsformular einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflowprojektelement hinzufügen, gestaltet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatisch die XML\-Datei in der Datei "Elements.xml" des Workflows um, um das Attribut beizubehalten, das auf das synchronisierte Zuordnungs\- oder Initiierungsformular verweist, wenn der Formularname bzw. Bereitstellungspfad aktualisiert oder das Formular gelöscht wird.  Wenn Sie jedoch andere Formulartypen in einem Workflow, z. B. ein Aufgaben\- oder Änderungsformular, verwenden, wird die Datei "Elements.xml" nicht umgestaltet.  
  
## Formularunterstützung für neue Visual Studio\-Workflows  
 In der folgenden Tabelle ist die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Unterstützung für unterschiedliche Formulartypen in ASPX\- bzw. InfoPath\-Formularen in Workflows aufgeführt, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt werden.  
  
|Formulartyp|In Visual Studio mit einem ASPX\-Formular erstellter Workflow|In Visual Studio mit einem InfoPath\-Formular erstellter Workflow|  
|-----------------|-------------------------------------------------------------------|-----------------------------------------------------------------------|  
|Zuordnung|-   Dem Workflow kann ein ASPX\-Zuordnungsformular mit der Elementvorlage **Workflowzuordnungsformular** hinzugefügt werden.<br />-   Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird, oder sich der Bereitstellungspfad ändert.<br />-   Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Es gibt keine InfoPath\-Zuordnungsformularvorlage in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Die Integration von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath\-Designer wird nicht unterstützt.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Initiierung|-   Dem Workflow kann ein ASPX\-Initiierungsformular mit der Elementvorlage **Workflowinitiierungsformular** hinzugefügt werden.<br />-   Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird, oder sich der Bereitstellungspfad ändert.<br />-   Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   Es gibt keine InfoPath\-Zuordnungsformularvorlage in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Die Integration von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath\-Designer wird nicht unterstützt.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Aufgabe|-   In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ist keine ASPX\-Aufgabenformularvorlage verfügbar.  Sie müssen eine Anwendungsseite erstellen und dieser dann Code hinzufügen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.<br />-   Weitere Informationen finden Sie unter [Workflow\-Aufgaben\-Formulare \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   Es gibt kein InfoPath\-Aufgabenformular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Die Integration von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath\-Designer wird nicht unterstützt.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Änderung|-   In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ist keine ASPX\-Änderungsformularvorlage verfügbar.  Sie müssen eine Anwendungsseite erstellen und dieser dann Code hinzufügen, um ein Änderungsformular hinzuzufügen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.  Sie müssen sie nach Bedarf manuell bearbeiten.<br />-   Weitere Informationen finden Sie unter [Workflow\-Änderungs\-Formulare \(SharePoint Foundation\)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   Es gibt keine InfoPath\-Änderungsformularvorlage in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   Die Integration von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath\-Designer wird nicht unterstützt.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
  
## Formularunterstützung in importierten, wiederverwendbaren SharePoint\-Workflows  
 In der folgenden Tabelle ist die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Unterstützung für unterschiedliche Formulartypen in ASPX\- bzw. InfoPath Formularen in wiederverwendbaren SharePoint\-Workflows aufgeführt, die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importiert werden.  
  
|Formulartyp|Wiederverwendbarer Workflow, der ein aus SharePoint Designer importiertes ASPX\-Formular aufweist|Wiederverwendbarer Workflow, der ein aus SharePoint Designer importiertes InfoPath\-Formular aufweist|  
|-----------------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|  
|Zuordnung|-   Auf das Formular wird in der Datei "Elements.xml" des Workflows verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird, oder sich der Bereitstellungspfad ändert.|-   Das Formular wird importiert, in der Datei "Elements.xml" des Workflows wird jedoch nicht darauf verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Initiierung|-   Auf das Formular wird vom Workflow in der Datei "Elements.xml" des Workflows verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird, oder sich der Bereitstellungspfad ändert.|-   Das Formular wird importiert, in der Datei "Elements.xml" des Workflows wird jedoch nicht darauf verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet. **Note:**  Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|  
|Aufgabe|-   Auf das Formular wird in der Datei "Elements.xml" des Workflows verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|-   Das Formular wird importiert, in der Datei "Elements.xml" des Workflows wird jedoch nicht darauf verwiesen.<br />-   Die Datei "Elements.xml" des Workflows wird nicht umgestaltet. **Note:**  Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|  
|Änderung|Nicht zutreffend.  ASPX\-Änderungsformulare können nicht in SharePoint Designer erstellt werden.|Nicht zutreffend.  InfoPath\-Änderungsformulare können nicht in SharePoint Designer erstellt werden, außer dem integrierten SharePoint Server\-Workflow, der nicht in der WSP\-Datei enthalten ist, wenn der Workflow exportiert wird.|  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  