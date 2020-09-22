---
title: Befehls Verfügbarkeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840852"
---
# <a name="command-availability"></a>Befehlsverfügbarkeit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Visual Studio-Kontext bestimmt, welche Befehle verfügbar sind. Der Kontext kann sich je nach dem aktuellen Projekt, dem aktuellen Editor, den geladenen VSPackages und anderen Aspekten der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) ändern.  
  
## <a name="command-contexts"></a>Befehls Kontexte  
 Die folgenden Befehls Kontexte sind am häufigsten.  
  
- **IDE** Von der IDE bereitgestellte Befehle sind immer verfügbar.  
  
- **VSPackage** VSPackages können definieren, wann Befehle angezeigt oder ausgeblendet werden sollen.  
  
- **Projekt** Projekt Befehle werden nur für das aktuell ausgewählte Projekt angezeigt.  
  
- **Editor** Es kann jeweils nur ein Editor aktiv sein. Befehle aus dem aktiven Editor sind verfügbar. Ein Editor funktioniert eng mit einem Sprachdienst. Der Sprachdienst muss seine Befehle im Kontext des zugehörigen Editors verarbeiten.  
  
- **Dateityp** Ein Editor kann mehr als einen Dateityp laden. Die verfügbaren Befehle können sich je nach Dateityp ändern.  
  
- **Aktives Fenster** Das letzte aktive Dokument Fenster legt den Kontext der Benutzeroberfläche (UI) für Tastenbindungen fest. Ein Tool Fenster, das über eine Schlüssel Bindungs Tabelle verfügt, die dem internen Webbrowser ähnelt, könnte jedoch auch den UI-Kontext festlegen. Für Dokument Fenster mit mehreren Registerkarten, wie z. b. den HTML-Editor, hat jede Registerkarte eine andere Befehls Kontext-GUID. Nachdem ein Tool Fenster registriert wurde, ist es immer im Menü **Ansicht** verfügbar.  
  
- **UI-Kontext** UI-Kontexte werden durch die Werte der- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Klasse identifiziert, z. b. <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> Wenn die Projekt Mappe erstellt wird oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> Wenn der Debugger aktiv ist. Mehrere UI-Kontexte können gleichzeitig aktiv sein.  
  
## <a name="defining-custom-context-guids"></a>Definieren von benutzerdefinierten Kontext-GUIDs  
 Wenn noch keine geeignete Befehls Kontext-GUID definiert ist, können Sie eine in Ihrem VSPackage definieren und diese dann so programmieren, dass Sie je nach Bedarf aktiv oder inaktiv ist, um die Sichtbarkeit der Befehle zu steuern.  
  
1. Registrieren Sie Kontext-GUIDs, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode aufrufen.  
  
2. Rufen Sie den Zustand einer Kontext-GUID ab, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode aufrufen.  
  
3. Aktivieren bzw. deaktivieren Sie Kontext-GUIDs, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode aufrufen.  
  
    > [!CAUTION]
    > Stellen Sie sicher, dass das VSPackage keine Auswirkungen auf vorhandene Kontext-GUIDs hat, da andere VSPackages von Ihnen abhängig sein können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswahl Kontext Objekte](../../extensibility/internals/selection-context-objects.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
