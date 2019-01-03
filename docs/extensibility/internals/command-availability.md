---
title: Befehl Verfügbarkeit | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ac9a172ee2cb7a117a1d9b63c4f1fef9f631952
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915865"
---
# <a name="command-availability"></a>Befehlsverfügbarkeit

Der Visual Studio-Kontext wird bestimmt, welche Befehle verfügbar sind. Je nach dem aktuellen Projekt, den aktuellen Editor, die VSPackages, die geladen werden und andere Aspekte der integrierten Entwicklungsumgebung (IDE) kann den Kontext zu ändern.

## <a name="command-contexts"></a>Befehlskontexte

Die folgenden Befehl Kontexten, die die häufigsten Ursachen sind:

- IDE-GERÄTE: Befehle, die von der IDE bereitgestellt sind immer verfügbar.

- VSPackage: VSPackages können definieren, wenn Befehle sind, angezeigt oder ausgeblendet werden.

- Projekt: Projektbefehle werden nur für das aktuell ausgewählte Projekt.

- Editor: Nur ein Editor kann jeweils aktiv sein. Befehle vom aktiven Editor zur Verfügung. Ein Editor arbeitet eng mit einem Sprachdienst. Der Sprachdienst muss die Befehle im Kontext des zugeordneten Editor verarbeiten.

- Dateityp: Ein Editor kann mehr als eine Art von Datei geladen werden. Die verfügbaren Befehle können je nach Dateityp ändern.

- Aktive Fenster: Die letzte aktive Fenster wird den Benutzerkontext für die Benutzeroberfläche (UI) für tastenzuordnungen. Ein Toolfenster, das eine Tabelle von Schlüssel-Bindung verfügt, die den internen Webbrowser ähnelt jedoch festlegen auch den UI-Kontext. Jede Registerkarte hat mit mehreren Registerkarten Dokumentfenster wie z. B. der HTML-Editor einen anderen Befehlskontext-GUID. Nach dem Registrieren eines Toolfensters ist es immer verfügbar, auf die **Ansicht** Menü.

- UI-Kontext: Benutzeroberfläche-Kontexte werden durch die Werte der identifiziert die <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Klasse, z. B. <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> , wenn die Projektmappe erstellt wird, oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> Wenn der Debugger aktiv ist. Mehrere UI-Kontext können gleichzeitig aktiv sein.

## <a name="define-custom-context-guids"></a>Definieren von benutzerdefinierten Kontext-GUIDs

Wenn einen entsprechenden Befehl-Kontext, den GUID noch nicht definiert ist, können Sie eine solche im VSPackage definieren, und klicken Sie dann Programmieren zu aktiven oder inaktiven nach Bedarf, um die Sichtbarkeit Ihrer Befehle zu steuern:

1.  Registrieren Sie die Kontext-GUIDs durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode.

2.  Rufen Sie den Status der Kontext-GUID durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode.

3.  Aktivieren Sie das Kontext-GUIDs und deaktivieren durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode.
   
> [!CAUTION]
> Stellen Sie sicher, dass Ihr VSPackage keine vorhandenen Kontext GUIDs auswirkt, da es sich bei anderen VSPackages möglicherweise von ihnen abhängig sind.

## <a name="see-also"></a>Siehe auch

- [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)