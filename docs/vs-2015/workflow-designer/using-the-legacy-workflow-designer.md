---
title: Verwenden des Legacy Workflow-Designer | Microsoft-Dokumentation
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

 Sie können darauf zugreifen, indem Sie in der Dropdown Liste am oberen Rand des Fensters **Neues Projekt** entweder die Option **.NET Framework 3,0** oder die Option **.NET Framework 3,5** auswählen. Die Standardoption in [!INCLUDE[vs2010](../includes/vs2010-md.md)] ist **.NET Framework 4** , die verwendet wird, um [!INCLUDE[wf](../includes/wf-md.md)] Anwendungen zu erstellen, die auf die [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]abzielen.

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] bietet eine Möglichkeit, [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen mithilfe der vertrauten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Benutzeroberfläche grafisch zu erstellen. [!INCLUDE[wf](../includes/wf-md.md)]-Anwendungen bestehen aus Workflowprozessschritten, den so genannten Aktivitäten. Um einen Workflow zu erstellen, verfassen Sie Aktivitäten auf der Entwurfs Oberfläche, indem Sie die entsprechenden Aktivitäts Designer aus der **Toolbox** auf die Entwurfs Oberfläche ziehen.

 In der folgenden Tabelle sind die wichtigsten Funktionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für Windows Workflow Foundation aufgeführt.

|Funktion|Beschreibung|
|-------------|-----------------|
|Drag &amp; Drop-Funktionalität für Aktivitäten|Ziehen Sie Aktivitäten aus der **Toolbox** auf die Entwurfs Oberfläche, um einen Workflow zu erstellen.|
|Eigenschaftenbrowser|Das Fenster Standard **Eigenschaften** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird verwendet, um die Eigenschaften einer Aktivität zu konfigurieren.|
|Zoom|Das Symbol für die **Zoomstufe** für die Auslassungs Zeichen befindet sich unterhalb der vertikalen Schiebe Leiste auf der rechten Seite der Entwurfs Oberfläche. Klicken Sie auf das fern Glas, und wählen Sie einen Zoom Prozentsatz aus, um die Workflow Grafik zu vergrößern oder zu verkleinern. Zum Vergrößern und verkleinern können Sie auch die Cursor Optionen für das **Schwenken** -Symbol vergrößern.|
|Schwenken|Das Schwenk Symbol, ein Kreis, der vier überquerte Pfeile enthält **, die in** vier Richtungen zeigen, befindet sich unterhalb der vertikalen Schiebe Leiste auf der rechten Seite der Entwurfs Oberfläche direkt unterhalb des Zoom Symbols für das fern Glas. Wenn Sie auf das Schwenksymbol klicken, erscheint ein Popupmenü mit den folgenden Cursoroptionen:<br /><br /> -Durch **Klicken auf die** Entwurfs Oberfläche können Sie mit dem Vergrößerungsglas Cursor vergrößern.<br />Mit dem Cursor **Zoom** -Lupe können Sie durch Klicken auf die Entwurfs Oberfläche verkleinern.<br />-Mithilfe des Hand Cursors des **Navigationstools** können Sie die Ansicht eines Workflows in der Entwurfs Oberfläche "durch fangen" und verschieben.<br />Mit dem **Standard** Pfeilcursor können Sie von den anderen Cursorn zurück zum Standardpfeil Cursor wechseln.|
|Autobildlauf|Wenn Sie über einen umfangreichen Workflow verfügen, möchten Sie möglicherweise eine Aktivität jenseits der sichtbaren Anzeige des Entwurfsoberflächenbereichs ablegen. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] unterstützt das Ziehen einer Aktivität an den Rand der Entwurfsoberfläche in die Nähe der Stelle, an der die Aktivität abgelegt werden soll. Die Entwurfsoberflächenansicht führt einen automatischen Bildlauf in diese Richtung durch.|
|Smarttags|Aktivitäten, die nicht vollständig konfiguriert oder nicht ordnungsgemäß konfiguriert sind, sind mit einem Ausrufezeichensymbol gekennzeichnet. Sie können auf das Symbol klicken, um eine Dropdownliste mit in der Aktivität vorhandenen Konfigurationsanforderungen aufzurufen. Sie können dann das Fenster **Eigenschaften** verwenden, um die Aktivität entsprechend zu konfigurieren. Wenn alle Eigenschaften für die Aktivität gültig sind, verschwindet das Ausrufezeichensymbol.|

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
 [Entwickeln von Workflows](https://go.microsoft.com/fwlink?LinkID=65010)