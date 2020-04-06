---
title: Befehle und Menüs, die Interop-Assemblys verwenden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709491"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden
Ein VSPackage, das Menü- und Symbolleistenbefehle mithilfe von Interop-Assemblys implementiert, muss:

- Informieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie die integrierte Entwicklungsumgebung (IDE) über die unterstützten Befehle und darüber, ob sie derzeit aktiviert sind.

- Halten Sie sich an die Regeln (Vertrag) für die Handhabung von Befehlen.

- Implementieren Sie die Befehlsbehandlung explizit mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder-Schnittstelle. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>

  Im folgenden Abschnitt wird beschrieben, wie diese Aufgaben ausgeführt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Beschreibt, wie ein VSPackage die IDE darüber benachrichtigt, welche Befehle es unterstützt und ob sie derzeit aktiviert sind.

- [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Stellt eine Definition des grundlegenden Befehlsvertrags bereit, der von allen VSPackages-Implementierungsbefehlen mithilfe von Interop-Assemblys verwendet wird.

- [Befehlsimplementierung](../../extensibility/internals/command-implementation.md)

 Bietet einen Überblick darüber, wie ein VSPackage einen Befehl implementiert.

- [Interop-Assemblybefehlshandler registrieren](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Beschreibt die Registrierungseinträge, die erforderlich sind, um die IDE zu benachrichtigen, dass ein VSPackage einen Befehlshandler bereitstellt.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)

 Beschreibt Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt sie verarbeitet.

- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Enthält Details zum Erstellen einer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, die Befehlsunterstützung verwendet.

- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Eine Übersicht über den Prozess, der verwendet wird, um ein Objekt mit der richtigen Befehlsanforderung zu verknüpfen.
