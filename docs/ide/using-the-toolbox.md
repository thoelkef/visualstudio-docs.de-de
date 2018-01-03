---
title: Verwenden der Toolbox | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c41a77a1fdb36ab8610ebc648cacb1568b330de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-toolbox"></a>Verwenden der Toolbox

Mithilfe des Werkzeugkastens können Sie Ihrem Projekt Steuerelemente und andere Elemente hinzufügen. Sie können verschiedene Steuerelemente per Drag & Drop auf die Oberfläche des verwendeten Designers verschieben und die Größe und Position der Steuerelemente ändern.

Der Werkzeugkasten wird in Verbindung mit Designeransichten angezeigt, wie der Entwurfsansicht einer XAML-Datei. Im Werkzeugkasten werden nur die Steuerelemente angezeigt, die im aktuellen Designer verwendet werden können.

Die in Ihrem Projekt verwendete .NET Framework-Version wirkt sich auch auf den Satz von Steuerelementen aus, der im Werkzeugkasten angezeigt wird. Sie können festlegen, dass Ihr Projekt eine andere Version von .NET Framework verwendet, indem Sie den Projektknoten im **Projektmappen-Explorer** auswählen und anschließend mit **Eigenschaften > Anwendung > Zielframework** durchsuchen.

## <a name="managing-the-toolbox-and-its-controls"></a>Verwalten der Toolbox und deren Steuerelemente

Standardmäßig wird die Toolbox auf der linken Seite der Visual Studio IDE reduziert dargestellt und wird angezeigt, wenn der Mauszeiger darüber bewegt wird. Sie können die Toolbox anheften (durch Klicken auf das Symbol **Anheften** auf der Toolbox-Symbolleiste), sodass dieser geöffnet bleibt, wenn Sie den Cursor verschieben. Sie können das Toolboxfenster auch abdocken und es an eine beliebige Stelle auf dem Bildschirm ziehen. Sie können den Werkzeugkasten andocken, abdocken und ausblenden, indem Sie mit der rechten Maustaste auf die Werkzeugkasten-Symbolleiste klicken und eine der Optionen auswählen.

Mithilfe der folgenden Befehle im Kontextmenü können Sie die Elemente auf einer Toolboxregisterkarte neu anordnen oder benutzerdefinierte Registerkarten und Elemente hinzufügen:

-   **Element umbenennen**: benennt das ausgewählte Element um.  
  
-   **Alle anzeigen**: zeigt alle möglichen Steuerelemente an (nicht nur die für den aktuellen Designer).  
  
-   **Listenansicht**: zeigt die Steuerelemente in einer vertikalen Liste an. Wenn dieses Kontrollkästchen deaktiviert ist, werden die Steuerelemente horizontal angezeigt.  
  
-   **Elemente auswählen**: öffnet das Dialogfeld **Toolboxelemente auswählen**, sodass Sie die Elemente festlegen können, die in der **Toolbox** angezeigt werden. Sie können ein Element ein- oder ausblenden, indem Sie dessen Kontrollkästchen aktivieren oder deaktivieren.  
  
-   **Elemente alphabetisch sortieren**: sortiert die Elemente nach Namen.  
  
-   **Symbolleiste zurücksetzen**: stellt die Standardeinstellungen des Werkzeugkastens und die Standardelemente wieder her.  
  
-   **Registerkarte hinzufügen**: fügt eine neue Werkzeugkasten-Registerkarte hinzu.  
  
-   **Nach oben**: verschiebt das ausgewählte Element nach oben.  
  
-   **Nach unten**: verschiebt das ausgewählte Element nach unten.  

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Erstellen und Verteilen von benutzerdefinierten Toolbox-Steuerelementen

Sie können ein benutzerdefiniertes Toolbox-Steuerelement in Visual Basic oder Visual C++ erstellen, und Sie können mit einer Projektvorlage beginnen, die auf [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) oder [Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md) basiert. Sie können Ihr Steuerelement dann an Ihre Teamkollegen verteilen oder es im Internet mithilfe des [Installationsprogramms für Toolbox-Steuerelemente](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx) veröffentlichen.

## <a name="see-also"></a>Siehe auch

[Schreiben von Code im Editor](../ide/writing-code-in-the-code-and-text-editor.md)