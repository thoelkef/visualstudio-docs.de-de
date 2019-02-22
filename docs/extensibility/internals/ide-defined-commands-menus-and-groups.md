---
title: IDE-definierte Befehle, Menüs und Gruppen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 727c999e275830260ce83eac3d2d72024e89882b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602376"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE-definierte Befehle, Menüs und Gruppen
Viele Menüs, Befehle und Befehlsgruppen sind bereits definiert, für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Diese Befehle stehen auch zur Verfügung, wenn Sie erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="finding-environment-defined-commands"></a>Umgebung-definierte Befehle Suchen
 Die umgebungsbefehle werden in einem Satz von vier VSCT-Dateien definiert:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Diese Dateien befinden sich im  *\<Visual Studio SDK-Installationspfad >* \VisualStudioIntegration\Common\Inc\\. Diese Dateien enthalten die Definitionen und die GUIDs der Menüs und Gruppen, die Sie in der Befehlsdatei für die Konfiguration (VSCT) von Tabelle Ihres VSPackage als Container für Ihre eigenen Menüs, Gruppen und Befehle verwenden können.

## <a name="in-this-section"></a>In diesem Abschnitt
- [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Gibt die GUID und ID-Werte von Menüs in der Visual Studio-Menüleiste, und der darin enthaltenen Gruppen.

- [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Gibt die GUID und ID-Werte, der in Symbolleisten in Visual Studio-IDE, und der darin enthaltenen Gruppen.

- [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Gibt die GUID und ID-Werte, der Befehle, die von der Visual Studio-IDE definiert sind.

## <a name="see-also"></a>Siehe auch
- [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)