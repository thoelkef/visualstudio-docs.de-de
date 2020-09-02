---
title: IDE-definierte Befehle, Menüs und Gruppen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192736"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Viele Menüs, Befehle und Befehls Gruppen sind bereits für die Verwendung durch die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE definiert. Diese Befehle sind auch für ihre Verwendung verfügbar, wenn Sie erweitern [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Suchen von Umgebungs definierten Befehlen  
 Die Umgebungs Befehle sind in einem Satz von vier vsct-Dateien definiert:  
  
- Sharedcmddef. vsct  
  
- Sharedcmdplace. vsct  
  
- Shellcmddef. vsct  
  
- Shellcmdplace. vsct  
  
  Diese Dateien befinden sich unter *\<Visual Studio SDK installation path>* \visualstudiointegration\common\inc \\ . Diese Dateien enthalten die Definitionen und GUIDs der Menüs und Gruppen, die Sie in der Befehls Tabellen Konfigurationsdatei (vsct-Datei) Ihres VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Gibt die GUID-und ID-Werte der Menüs in der Visual Studio-Menüleiste und der Gruppen an, die Sie enthalten.  
  
 [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Gibt die GUID-und ID-Werte von Symbolleisten in der Visual Studio-IDE und der darin enthaltenen Gruppen an.  
  
 [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Gibt die GUID-und ID-Werte von Befehlen an, die von der Visual Studio-IDE definiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio-Befehls Tabelle (. Vsct-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [IDE-definierte Befehle zum Erweitern von Projekt Systemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
