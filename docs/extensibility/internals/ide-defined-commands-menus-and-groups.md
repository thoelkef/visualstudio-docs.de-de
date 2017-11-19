---
title: "IDE-definierte Befehle, Menüs und Gruppen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 032baaa57dd91cb07eac547da810d16e708f0828
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
Viele Menüs, Befehle und Befehlsgruppen bereits definiert, für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Diese Befehle stehen auch für die Verwendung verfügbar, wenn Sie erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Suchen die Umgebung definiert Befehle  
 Die Umgebung Befehle sind in einem Satz von vier VSCT-Dateien definiert:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Diese Dateien befinden sich im  *\<Visual Studio SDK-Installationspfad >*\VisualStudioIntegration\Common\Inc\\. Diese Dateien enthalten die Definitionen und die GUIDs der Menüs und Gruppen, die Sie in der Befehlsdatei für die Konfiguration (VSCT) von Tabelle Ihres VSPackage als Container für Menüs, Gruppen und Befehle verwenden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Gibt die GUID und ID-Werte von Menüs, die in der Visual Studio-Menüleiste, und der darin enthaltenen Gruppen.  
  
 [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Gibt die GUID und ID-Werte von Symbolleisten in Visual Studio-IDE und der darin enthaltenen Gruppen.  
  
 [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Gibt die GUID und ID-Werte von Befehlen, die von der Visual Studio-IDE definiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)