---
title: Mithilfe des Legacy-Workflow-Designers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: "10"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: eda078bdfc0eae8861ac4e70b0f1f73a399f994c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="using-the-legacy-workflow-designer"></a>Verwenden des Legacyworkflow-Designers
Die von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] bereitgestellte Vorgängerversion von [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] kann verwendet werden, um auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzuzielen.  
  
 Zugriff darauf ist möglich durch Aktivieren der **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster. Die Standardoption in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ist **.NET Framework 4** dient zum Erstellen [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] Anwendungen, die als Ziel der [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] bietet eine Möglichkeit, [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen mithilfe der vertrauten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Benutzeroberfläche grafisch zu erstellen. [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen bestehen aus Workflowprozessschritten, den so genannten Aktivitäten. Um einen Workflow zu erstellen, erstellen Sie Aktivitäten auf der Entwurfsoberfläche ziehen Sie die jeweiligen Aktivitätsdesigner aus **Toolbox** auf die Entwurfsoberfläche.  
  
 In der folgenden Tabelle sind die wichtigsten Funktionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für Windows Workflow Foundation aufgeführt.  
  
|Funktion|Beschreibung|  
|-------------|-----------------|  
|Drag & Drop-Funktionalität für Aktivitäten|Ziehen Sie Aktivitäten aus der **Toolbox** auf die Entwurfsoberfläche zum Erstellen eines Workflows.|  
|Eigenschaftenbrowser|Der Standard **Eigenschaften** Fenster in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird verwendet, um die Eigenschaften einer Aktivität zu konfigurieren.|  
|Zoom|Das fernglassymbol **Zoomebene** Symbol befindet sich unterhalb der vertikalen Bildlaufleiste auf der rechten Seite der Entwurfsoberfläche angezeigt. Klicken Sie auf das Fernglas, und wählen Sie einen Prozentsatz für den Zoom aus, um die Workflowgrafik zu vergrößern beziehungsweise zu verkleinern. Sie können auch die **Schwenken** Symbol Vergrößerungsglas Cursoroptionen zum Vergrößern und verkleinern.|  
|Schwenken|Die **Schwenken** Symbol, ein Kreis mit vier sich kreuzenden und in vier Richtungen weisenden Pfeilen, befindet sich unterhalb der vertikalen Bildlaufleiste auf der rechten Seite der Entwurfsoberfläche direkt unterhalb des Zoom-fernglassymbols. Wenn Sie auf das Schwenksymbol klicken, erscheint ein Popupmenü mit den folgenden Cursoroptionen:<br /><br /> – Der **vergrößern** -lupencursor können Sie vergrößern, indem Sie auf der Entwurfsoberfläche angezeigt.<br />– Der **verkleinern** -lupencursor können Sie verkleinern, indem Sie auf der Entwurfsoberfläche angezeigt.<br />– Der **Navigationstool** -Handcursor können Sie die "greifen" und verschieben Sie die Ansicht eines Workflows in der Entwurfsoberfläche angezeigt.<br />– Der **Standard** -Pfeilcursor können Sie von anderen Cursorn zurück zum Standardpfeilcursor wechseln.|  
|Autobildlauf|Wenn Sie über einen umfangreichen Workflow verfügen, möchten Sie möglicherweise eine Aktivität jenseits der sichtbaren Anzeige des Entwurfsoberflächenbereichs ablegen. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] unterstützt das Ziehen einer Aktivität an den Rand der Entwurfsoberfläche in die Nähe der Stelle, an der die Aktivität abgelegt werden soll. Die Entwurfsoberflächenansicht führt einen automatischen Bildlauf in diese Richtung durch.|  
|Smarttags|Aktivitäten, die nicht vollständig konfiguriert oder nicht ordnungsgemäß konfiguriert sind, sind mit einem Ausrufezeichensymbol gekennzeichnet. Sie können auf das Symbol klicken, um eine Dropdownliste mit in der Aktivität vorhandenen Konfigurationsanforderungen aufzurufen. Anschließend können Sie die **Eigenschaften** Fenster entsprechend die Aktivität konfigurieren. Wenn alle Eigenschaften für die Aktivität gültig sind, verschwindet das Ausrufezeichensymbol.|  
  
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
 [Entwickeln von Workflows](http://go.microsoft.com/fwlink?LinkID=65010)