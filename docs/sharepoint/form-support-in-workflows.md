---
title: Unterstützung in Workflows bilden | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 704e08524bb9aaf014dbd29e7df7361a7e1bbefe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604131"
---
# <a name="form-support-in-workflows"></a>Unterstützung von Formularen in workflows
  Vier Arten von Formularen in einem Workflow verwendet werden können: Zuordnung, Initiierung, Aufgabe und Änderung. Dieser Formulartypen können auf eine ASPX-Webformular oder ein InfoPath-Formular basieren. Die Ebene der Unterstützung, die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bietet für verschiedene Faktoren berücksichtigt, ein bestimmtes Formulars hängt die in der folgenden Tabelle beschrieben werden. Weitere Informationen zu den Workflow-Formulartypen, finden Sie unter [Workflow Forms Overview](http://go.microsoft.com/fwlink/?LinkId=185228).

## <a name="xml-refactoring"></a>XML-refactoring
 Wenn Sie eine ASPX-Zuordnungs- oder ein Formular zum Hinzufügen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow-Projektelement, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatisch gestaltet die Workflow XML- *"Elements.xml"* Datei das Attribut beibehalten wird, die auf die Zuordnung verweist oder Initiierungsformular synchron bei jeder Aktualisierung der Form Name oder die Bereitstellung der Pfad oder das Formular gelöscht wird. Allerdings bei Verwendung anderer Arten von Formularen in einem Workflow, z. B. einen Task oder Änderung, die *"Elements.xml"* Datei ist nicht umgestaltet.

## <a name="form-support-in-new-visual-studio-workflows"></a>Unterstützung von in die neue Visual Studio-workflows
 Die folgende Tabelle enthält [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unterstützung für verschiedene Datentypen auf ASPX- bzw. InfoPath-Formularen in Workflows, die erstellt werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Formulartyp|Workflow mit einer ASPX-Webformular in Visual Studio erstellt wurde|Workflow in Visual Studio erstellt wurde, mithilfe von einem InfoPath-Formular|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Zuordnung|-Eine ASPX-Zuordnungsformular kann an den Workflow hinzugefügt werden, mithilfe der **Workflowzuordnungsformular** Elementvorlage.<br />– Die *"Elements.xml"* Datei des Workflows wird umgestaltet werden, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird, oder der Bereitstellungspfad ändert.<br />-Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Es gibt keine Zuordnung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|
|Initiierung|-Eine ASPX-Initiierungsformular kann an den Workflow hinzugefügt werden, mithilfe der **Workflowinitiierungsformular** Elementvorlage.<br />– Die *"Elements.xml"* Datei des Workflows wird umgestaltet werden, wenn das Formular hinzugefügt, umbenannt oder gelöscht wird, oder der Bereitstellungspfad ändert.<br />-Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|– Es gibt keine Zuordnung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|
|Aufgabe|– Keine ASPX-Formular Aufgabenvorlage steht in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sie müssen eine Anwendungsseite erstellen und fügen Sie Code hinzu.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.<br />-Weitere Informationen finden Sie unter [Aufgabe Workflowformulare (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|– Es gibt keine Aufgabe InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|
|Änderung|– Keine Formularvorlage der ASPX-Änderung steht in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Um eine Änderungsformular hinzuzufügen, müssen Sie eine Anwendungsseite erstellen und fügen Sie Code hinzu.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet. Sie müssen Sie manuell nach Bedarf bearbeiten.<br />-Weitere Informationen finden Sie unter [Änderungsformulare "Workflow" (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|– Es ist keine Änderung InfoPath-Formular in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />– Es ist keine Integration zwischen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und InfoPath-Designer.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Unterstützung von Formularen in den wiederverwendbaren SharePoint-workflows
 Die folgende Tabelle enthält [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unterstützung für andere Typen in entweder ASPX- oder InfoPath-Formularen in wiederverwendbaren SharePoint-Workflows, die in importiert werden [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Formulartyp|Wiederverwendbaren Workflows, der eine ASPX-Webformular aus SharePoint Designer importiert wurde.|Wiederverwendbaren Workflows, der ein InfoPath-Formular, das von SharePoint Designer importiert wurde.|
|---------------|-------------------------------------------------------------------------------| - |
|Zuordnung|-Das Formular verwiesen wird, der *"Elements.xml"* Datei des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird umgestaltet werden, wenn das Formular umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.|-Das Formular wird importiert, jedoch keinen Verweis auf die *"Elements.xml"* des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|
|Initiierung|-Das Formular wird verwiesen, indem der Workflow in den *"Elements.xml"* Datei des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird umgestaltet werden, wenn das Formular umbenannt oder gelöscht wird oder wenn sich der Bereitstellungspfad ändert.|-Das Formular wird importiert, jedoch keinen Verweis auf die *"Elements.xml"* des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet. **Hinweis**:  Regeln und Eigenschaften müssen hinzugefügt und für dieses Szenario geändert werden.|
|Aufgabe|-Das Formular verwiesen wird, der *"Elements.xml"* Datei des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet.|-Das Formular wird importiert, jedoch keinen Verweis auf die *"Elements.xml"* des Workflows.<br />– Die *"Elements.xml"* Datei des Workflows wird nicht umgestaltet. **Hinweis**:  Regeln und Eigenschaften müssen hinzugefügt und für dieses Szenario geändert werden.|
|Änderung|Nicht zutreffend. ASPX-Änderungsformulare können nicht in SharePoint Designer erstellt werden.|Nicht zutreffend. Änderungsformulare InfoPath können außer den integrierten SharePoint-Server-Workflow, die nicht in der .wsp-Datei enthalten ist, wenn der Workflow exportiert wird, in SharePoint Designer erstellt werden.|

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
