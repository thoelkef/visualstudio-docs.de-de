---
title: IDE-definierte Befehle, Menüs und Gruppen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727297"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
Viele Menüs, Befehle und Befehls Gruppen sind bereits für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE definiert. Diese Befehle sind auch für ihre Verwendung verfügbar, wenn Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erweitern.

## <a name="finding-environment-defined-commands"></a>Suchen von Umgebungs definierten Befehlen
 Die Umgebungs Befehle sind in einem Satz von vier vsct-Dateien definiert:

- Sharedcmddef. vsct

- Sharedcmdplace. vsct

- Shellcmddef. vsct

- Shellcmdplace. vsct

  Diese Dateien befinden sich im *\<Visual Studio SDK-Installationspfad >* \visualstudiointegration\common\inc \\. Diese Dateien enthalten die Definitionen und GUIDs der Menüs und Gruppen, die Sie in der Befehls Tabellen Konfigurationsdatei (vsct-Datei) Ihres VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.

## <a name="in-this-section"></a>In diesem Abschnitt
- [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Gibt die GUID-und ID-Werte der Menüs in der Visual Studio-Menüleiste und der Gruppen an, die Sie enthalten.

- [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Gibt die GUID-und ID-Werte von Symbolleisten in der Visual Studio-IDE und der darin enthaltenen Gruppen an.

- [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Gibt die GUID-und ID-Werte von Befehlen an, die von der Visual Studio-IDE definiert werden.

## <a name="see-also"></a>Siehe auch
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)