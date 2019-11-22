---
title: Using the Legacy Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302792"
---
# <a name="using-the-legacy-workflow-designer"></a>Verwenden des Legacyworkflow-Designers
Die von [!INCLUDE[wfd2](../includes/wfd2-md.md)] bereitgestellte Vorgängerversion von [!INCLUDE[vs2010](../includes/vs2010-md.md)] kann verwendet werden, um auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzuzielen.

 It is accessed by selecting either the **.NET Framework 3.0** option or the **.NET Framework 3.5** option in the drop down list at the top of the **New Project** window. The default option in [!INCLUDE[vs2010](../includes/vs2010-md.md)] is **.NET Framework 4** which is used to create [!INCLUDE[wf](../includes/wf-md.md)] applications that target the [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] bietet eine Möglichkeit, [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen mithilfe der vertrauten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Benutzeroberfläche grafisch zu erstellen. [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen bestehen aus Workflowprozessschritten, den so genannten Aktivitäten. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 In der folgenden Tabelle sind die wichtigsten Funktionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für Windows Workflow Foundation aufgeführt.

|Feature|Beschreibung|
|-------------|-----------------|
|Drag &amp; Drop-Funktionalität für Aktivitäten|Drag activities from the **Toolbox** onto the design surface to create a workflow.|
|Eigenschaftenbrowser|The standard **Properties** window in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] is used to configure the properties of an activity.|
|Zoom|The binoculars **Zoom Level** icon is located below the vertical scroll bar on the right side of the design surface. Click the binoculars and select a zoom percentage to cause the workflow graphic to zoom in or out. You can also use the **Pan** icon magnifying glass cursor options to zoom in and out.|
|Schwenken|The **Pan** icon, a circle that contains four crossed arrows pointing in four directions, is located below the vertical scroll bar on the right side of the design surface just below the binoculars zoom icon. Wenn Sie auf das Schwenksymbol klicken, erscheint ein Popupmenü mit den folgenden Cursoroptionen:<br /><br /> -   The **Zoom In** magnifying glass cursor lets you zoom in by clicking the design surface.<br />-   The **Zoom Out** magnifying glass cursor lets you zoom out by clicking the design surface.<br />-   The **Navigation Tool** hand cursor lets you "grab" and shift the view of a workflow in the design surface.<br />-   The **Default** arrow cursor lets you switch from the other cursors back to the default arrow cursor.|
|Autobildlauf|Wenn Sie über einen umfangreichen Workflow verfügen, möchten Sie möglicherweise eine Aktivität jenseits der sichtbaren Anzeige des Entwurfsoberflächenbereichs ablegen. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unterstützt das Ziehen einer Aktivität an den Rand der Entwurfsoberfläche in die Nähe der Stelle, an der die Aktivität abgelegt werden soll. Die Entwurfsoberflächenansicht führt einen automatischen Bildlauf in diese Richtung durch.|
|Smarttags|Aktivitäten, die nicht vollständig konfiguriert oder nicht ordnungsgemäß konfiguriert sind, sind mit einem Ausrufezeichensymbol gekennzeichnet. Sie können auf das Symbol klicken, um eine Dropdownliste mit in der Aktivität vorhandenen Konfigurationsanforderungen aufzurufen. You can then use the **Properties** window to configure the activity appropriately. Wenn alle Eigenschaften für die Aktivität gültig sind, verschwindet das Ausrufezeichensymbol.|

## <a name="in-this-section"></a>In diesem Abschnitt
 [Visual Studio-Workflowfenster (Vorgängerversion)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)

 [Sequenzielle Workflowansichten (Vorgängerversion)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)

 [Verwenden von Designs in Workflows (Vorgängerversion)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Verwenden des Zustandsautomatworkflow-Designers der Vorgängerversion](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Verwenden des Aktivitätsdesigners der Vorgängerversion](../workflow-designer/using-the-legacy-activity-designer.md)

 [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Siehe auch
 [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010)