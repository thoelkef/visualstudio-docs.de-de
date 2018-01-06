---
title: "Unterstützung in Workflows bilden | Microsoft Docs"
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
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0da90955a590881a02117213246e580339dbe596
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="form-support-in-workflows"></a>Unterstütung von Formularen in Workflows
  In einem Workflow können vier Typen von Formularen verwendet werden: Zuordnung, Initiierung, Aufgabe und Änderung. Diese Formulartypen können auf eine ASPX-Formular oder ein InfoPath-Formular basieren. Das Maß an Unterstützung, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält die sich auf eine bestimmte Form von mehreren Faktoren ab, abhängig ist die in den folgenden Tabellen beschrieben werden. Weitere Informationen zum Formular Workflowtypen finden Sie unter [Workflow Forms Overview](http://go.microsoft.com/fwlink/?LinkId=185228) auf der MSDN-Website.  
  
## <a name="xml-refactoring"></a>XML-Umgestaltung  
 Beim Hinzufügen einer ASPX-Zuordnung oder Einleitung Formular eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow-Projektelement, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatisch umgestaltet XML in der Workflowdatei "Elements.xml", um das Attribut beibehalten, die auf das Formular Zuordnung oder Einleitung synchron verweist Sobald der Pfad der Form Name oder Bereitstellung aktualisiert wird, oder das Formular gelöscht wird. Allerdings wird bei der Verwendung von anderen Arten von Formularen in einem Workflow, beispielsweise ein Formular Aufgabe oder Änderung der Datei "Elements.xml" nicht umgestaltet.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Unterstütung von Formularen in neuen Visual Studio-Workflows  
 Die folgende Tabelle enthält [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unterstützung für verschiedene Typen in ASPX- oder InfoPath-Formularen in Workflows, die in erstellt werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Formulartyp|Workflow erstellt, die in Visual Studio mit einem ASPX-Formular|Mithilfe eines InfoPath-Formulars in Visual Studio erstellte Workflows|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Zuordnung|-Eine ASPX-Zuordnungsformular kann an den Workflow hinzugefügt werden, mithilfe der **Workflow Zuordnungsformular** Elementvorlage.<br />-Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.<br />-Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Es ist keine Zuordnung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es gibt keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Initiierung|-Eine ASPX-Initiierung von Formular kann an den Workflow hinzugefügt werden, mithilfe der **Workflow Initiierungsformular** Elementvorlage.<br />-Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.<br />-Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Es ist keine Zuordnung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es gibt keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Aufgabe|– Keine ASPX-Formular Aufgabenvorlage steht in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sie müssen eine Anwendungsseite erstellen und Code hinzufügen.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.<br />-Weitere Informationen finden Sie unter [Workflow Taskformularen (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|– Es ist keine Aufgabe InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es gibt keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Änderung|– Keine ASPX Änderungsformularvorlage steht in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Um eine Änderungsformular hinzuzufügen, müssen Sie eine Anwendungsseite erstellen und Code hinzufügen.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet. Sie müssen Sie manuell nach Bedarf bearbeiten.<br />-Weitere Informationen finden Sie unter [Workflow Änderung Forms (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|– Es ist keine Änderung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es gibt keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Unterstütung von Formularen in importierten SharePoint Wiederverwendbaren Workflows  
 Die folgende Tabelle enthält [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unterstützung für verschiedene Typen in ASPX- oder InfoPath-Formularen in wiederverwendbaren SharePoint-Workflows, die in importiert sind [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Formulartyp|Wiederverwendbaren Workflows, der eine ASPX-Formular, das von SharePoint Designer importiert wurde.|Wiederverwendbaren Workflows, der ein InfoPath-Formular, das von SharePoint Designer importiert wurde.|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Zuordnung|-Das Formular wird in der Datei "Elements.xml" des Workflows verwiesen.<br />-Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.|-Das Formular wird importiert, jedoch nicht in der Datei "Elements.xml" des Workflows verwiesen wird.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|  
|Initiierung|-Das Formular wird vom Workflow in der Datei "Elements.xml" des Workflows verwiesen.<br />-Die Datei "Elements.xml" des Workflows wird umgestaltet, wenn das Formular umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.|-Das Formular wird importiert, jedoch nicht in der Datei "Elements.xml" des Workflows verwiesen wird.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet. **Hinweis:** Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|  
|Aufgabe|-Das Formular wird in der Datei "Elements.xml" des Workflows verwiesen.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet.|-Das Formular wird importiert, jedoch nicht in der Datei "Elements.xml" des Workflows verwiesen wird.<br />-Die Datei "Elements.xml" des Workflows wird nicht umgestaltet. **Hinweis:** Regeln und Eigenschaften müssen hinzugefügt und geändert werden, damit dieses Szenario funktioniert.|  
|Änderung|Nicht zutreffend. Aspx-Änderungsformulare können im SharePoint-Designer erstellt werden.|Nicht zutreffend. Änderung von Formularen können nicht im SharePoint-Designer, mit Ausnahme der integrierte SharePoint-Server-Workflow erstellt werden, die nicht in der WSP-Datei enthalten ist, wenn der Workflow exportiert wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  