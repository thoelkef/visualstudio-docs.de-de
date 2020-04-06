---
title: Befehlsverfügbarkeit | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709697"
---
# <a name="command-availability"></a>Befehlsverfügbarkeit

Der Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind. Der Kontext kann sich je nach aktuellem Projekt, dem aktuellen Editor, den geladenen VSPackages und anderen Aspekten der integrierten Entwicklungsumgebung (IDE) ändern.

## <a name="command-contexts"></a>Befehlskontexte

Die folgenden Befehlskontexte sind die häufigsten:

- IDE: Befehle, die von der IDE bereitgestellt werden, sind immer verfügbar.

- VSPackage: VSPackages kann definieren, wann Befehle angezeigt oder ausgeblendet werden sollen.

- Projekt: Projektbefehle werden nur für das aktuell ausgewählte Projekt angezeigt.

- Editor: Es kann jeweils nur ein Editor aktiv sein. Befehle aus dem aktiven Editor sind verfügbar. Ein Redakteur arbeitet eng mit einem Sprachdienst zusammen. Der Sprachdienst muss seine Befehle im Kontext des zugehörigen Editors verarbeiten.

- Dateityp: Ein Editor kann mehr als einen Dateityp laden. Die verfügbaren Befehle können sich je nach Dateityp ändern.

- Aktives Fenster: Das letzte aktive Dokumentfenster legt den Kontext der Benutzeroberfläche für Schlüsselbindungen fest. Ein Toolfenster mit einer Schlüsselbindungstabelle, die dem internen Webbrowser ähnelt, kann jedoch auch den UI-Kontext festlegen. Für Dokumentfenster mit mehreren Tab-Betten, z. B. den HTML-Editor, verfügt jede Registerkarte über eine andere Befehlskontext-GUID. Nachdem ein Toolfenster registriert wurde, ist es immer im Menü **Ansicht** verfügbar.

- UI-Kontext: UI-Kontexte werden durch <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> die Werte <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> der Klasse identifiziert, z. B. wenn die Lösung erstellt wird oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> wenn der Debugger aktiv ist. Mehrere UI-Kontexte können gleichzeitig aktiv sein.

## <a name="define-custom-context-guids"></a>Definieren benutzerdefinierter Kontext-GUIDs

Wenn eine entsprechende Befehlskontext-GUID noch nicht definiert ist, können Sie eine in Ihrem VSPackage definieren und sie dann so programmieren, dass sie aktiv oder inaktiv ist, um die Sichtbarkeit Ihrer Befehle zu steuern:

1. Registrieren Sie Kontext-GUIDs, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode aufrufen.

2. Rufen Sie den Status einer Kontext-GUID ab, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode aufrufen.

3. Aktivieren und deaktivieren Sie Kontext-GUIDs, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode aufrufen.

> [!CAUTION]
> Stellen Sie sicher, dass Ihr VSPackage keine vorhandenen Kontext-GUIDs beeinflusst, da andere VSPackages möglicherweise davon abhängen.

## <a name="see-also"></a>Weitere Informationen

- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
