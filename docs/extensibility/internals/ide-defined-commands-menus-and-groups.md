---
title: IDE-definierte Befehle, Menüs und Gruppen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707717"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
Viele Menüs, Befehle und Befehlsgruppen sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bereits für die Verwendung durch die IDE definiert. Diese Befehle stehen auch für Ihre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Verwendung zur Verfügung, wenn Sie erweitern.

## <a name="finding-environment-defined-commands"></a>Suchen von umgebungsdefinierten Befehlen
 Die Umgebungsbefehle werden in einem Satz von vier .vsct-Dateien definiert:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Diese Dateien befinden sich im\\ * \<Installationspfad von Visual Studio SDK>*. Diese Dateien stellen die Definitionen und GUIDs der Menüs und Gruppen bereit, die Sie in der Befehlstabellenkonfigurationsdatei (.vsct) Ihres VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.

## <a name="in-this-section"></a>In diesem Abschnitt
- [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Gibt die GUID- und ID-Werte von Menüs in der Visual Studio-Menüleiste und der enthaltenen Gruppen an.

- [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Gibt die GUID- und ID-Werte von Symbolleisten in der Visual Studio-IDE und der darin enthaltenen Gruppen an.

- [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Gibt die GUID- und ID-Werte von Befehlen an, die von der Visual Studio-IDE definiert wurden.

## <a name="see-also"></a>Weitere Informationen
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
