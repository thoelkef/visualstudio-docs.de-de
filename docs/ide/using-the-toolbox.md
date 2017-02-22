---
title: "Verwenden der Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.chooseitems"
  - "vs.toolboxpages.activexcontrols"
  - "VS.CHOOSEITEMS.windowsuixamlcomponents"
  - "VS.chooseitems.silverlightcomponents"
  - "VC.EDITORS.RIBBON"
  - "vs.customizetoolbox"
  - "VS.chooseitems.System.Workflow_Components"
  - "vs.chooseitems.frameworkcomponents"
  - "VS.ToolboxPages..NET_Framework_Components"
  - "VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage"
  - "vs.chooseitems.comcomponents"
  - "vs.toolboxpages.NGWS_components"
helpviewer_keywords: 
  - "Toolbox"
  - "Toolbox, Hinzufügen von Elementen"
  - "Toolbox, Registerkarten"
  - "Visual Studio, Toolbox"
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Verwenden der Toolbox
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe des Werkzeugkastens können Sie Ihrem Projekt Steuerelemente und andere Elemente hinzufügen.  Sie können verschiedene Steuerelemente per Drag & Drop auf die Oberfläche des verwendeten Designers verschieben und die Größe und Position der Steuerelemente ändern.  
  
 Der Werkzeugkasten wird in Verbindung mit Designeransichten angezeigt, wie der Entwurfsansicht einer XAML\-Datei.  Im Werkzeugkasten werden nur die Steuerelemente angezeigt, die im aktuellen Designer verwendet werden können.  
  
 Die in Ihrem Projekt verwendete .NET Framework\-Version wirkt sich auch auf den Satz von Steuerelementen aus, der im Werkzeugkasten angezeigt wird.  Standardmäßig verwenden [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]\-Projekte das .NET Framework 4.5.1.  Sie können festlegen, dass Ihr Projekt eine andere Version von .NET Framework verwendet, indem Sie den Projektknoten im **Projektmappen\-Explorer** auswählen und anschließend mit **Eigenschaften \> Anwendung \> Zielframework** durchsuchen.  
  
## Verwalten des Werkzeugkastens und dessen Steuerelemente  
 Standardmäßig ist der Werkzeugkasten auf der linken Seite der Visual Studio IDE reduziert dargestellt und wird angezeigt, wenn der Mauszeiger darüber bewegt wird.  Sie können den Werkzeugkasten anheften \(durch Klicken auf das Symbol **Anheften** auf der Werkzeugkasten\-Symbolleiste\), sodass dieser geöffnet bleibt, wenn Sie den Cursor verschieben.  Sie können das Werkzeugkastenfenster auch abdocken und es an eine beliebige Stelle auf dem Bildschirm ziehen.  Sie können den Werkzeugkasten andocken, abdocken und ausblenden, indem Sie mit der rechten Maustaste auf die Werkzeugkasten\-Symbolleiste klicken und eine der Optionen auswählen.  
  
 Mithilfe der folgenden Befehle im Kontextmenü können Sie die Elemente auf einer Werkzeugkasten\-Registerkarte neu anordnen oder benutzerdefinierte Registerkarten und Elemente hinzufügen:  
  
-   **Element umbenennen** – benennt das ausgewählte Element um.  
  
-   **Alle anzeigen** – zeigt alle möglichen Steuerelemente an \(nicht nur die für den aktuellen Designer\).  
  
-   **Listenansicht** \- zeigt die Steuerelemente in einer vertikalen Liste an.  Wenn dieses Kontrollkästchen deaktiviert ist, werden die Steuerelemente horizontal angezeigt.  
  
-   **Elemente auswählen** – öffnet das Dialogfeld **Werkzeugkastenelemente auswählen**, sodass Sie die Elemente festlegen können, die im **Werkzeugkasten** angezeigt werden.  Sie können ein Element ein\- oder ausblenden, indem Sie dessen Kontrollkästchen aktivieren oder deaktivieren.  
  
-   **Elemente alphabetisch sortieren** – sortiert die Elemente nach Namen.  
  
-   **Symbolleiste zurücksetzen** – stellt die Standardeinstellungen des Werkzeugkastens und die Standardelemente wieder her.  
  
-   **Registerkarte hinzufügen** – fügt eine neue Werkzeugkasten\-Registerkarte hinzu.  
  
-   **Nach oben** – verschiebt das ausgewählte Element nach oben.  
  
-   **Nach unten** – verschiebt das ausgewählte Element nach unten.  
  
## Erstellen und Verteilen von benutzerdefinierten Werkzeugkasten\-Steuerelementen  
 Sie können ein benutzerdefiniertes Werkzeugkasten\-Steuerelement in Visual Basic oder Visual C\+\+ erstellen, und Sie können mit einer Projektvorlage beginnen, die auf [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) oder [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) basiert.  Sie können dann das Steuerelement an Ihre Teamkollegen verteilen oder es im Internet veröffentlichen; verwenden Sie dazu den [Installer für Werkzeugkasten\-Steuerelemente](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).