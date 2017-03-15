---
title: "IDE-definierte Befehle, Men&#252;s und Gruppen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, die Umgebung definiert"
  - "VSCT-Dateien, Umgebung benutzerdefinierte Konstanten"
  - "Befehlsgruppen Umgebung definiert"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# IDE-definierte Befehle, Men&#252;s und Gruppen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Viele Menüs, Befehle und Befehlsgruppen sind bereits definiert, für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Diese Befehle stehen auch zur Verfügung, wenn Sie erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Suchen von Umgebung benutzerdefinierte Befehle  
 Die Umgebung Befehle werden in einem Satz von vier VSCT\-Dateien definiert:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Diese Dateien befinden sich im *\< Visual Studio SDK\-Installationspfad \>*\\VisualStudioIntegration\\Common\\Inc\\. Diese Dateien enthalten die Definitionen und GUIDs Menüs und Gruppen, die Sie in der Tabelle Configuration \(VSCT\)\-Befehlsdatei von Ihr VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.  
  
## In diesem Abschnitt  
 [GUIDs und IDs der Visual Studio\-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Gibt die GUID und ID\-Werte von Menüs in der Visual Studio\-Menüleiste und die darin enthaltenen Gruppen aus.  
  
 [GUIDs und IDs der Visual Studio\-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Gibt die GUID und ID\-Werte von Symbolleisten in Visual Studio\-IDE und die darin enthaltenen Gruppen aus.  
  
 [GUIDs und IDs der Visual Studio\-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Gibt die GUID und ID\-Werte von Befehlen, die von Visual Studio\-IDE definiert.  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE\-definierte Befehle für die Erweiterung Projektsysteme](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)