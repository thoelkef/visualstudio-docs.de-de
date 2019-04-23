---
title: Befehl Verfügbarkeit | Microsoft-Dokumentation
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
ms.openlocfilehash: 56aeb6a43cea18513a422741289a08a5b7c901c5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084234"
---
# <a name="command-availability"></a>Befehlsverfügbarkeit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Visual Studio-Kontext wird bestimmt, welche Befehle verfügbar sind. Je nach dem aktuellen Projekt, den aktuellen Editor, die VSPackages, die geladen werden und andere Aspekte der integrierten Entwicklungsumgebung (IDE) kann den Kontext zu ändern.  
  
## <a name="command-contexts"></a>Befehlskontexte  
 Der folgende befehlskontexte sind die häufigsten.  
  
- **IDE** Befehle, die von der IDE bereitgestellt sind immer verfügbar.  
  
- **VSPackage** VSPackages können definieren, wenn Befehle angezeigt oder ausgeblendet werden.  
  
- **Projekt** Projektbefehle werden nur für das aktuell ausgewählte Projekt angezeigt.  
  
- **Editor** nur ein Editor kann jeweils aktiv sein. Befehle vom aktiven Editor zur Verfügung. Ein Editor arbeitet eng mit einem Sprachdienst. Der Sprachdienst muss die Befehle im Kontext des zugeordneten Editor verarbeiten.  
  
- **Dateityp** ein Editor kann mehr als eine Art von Datei laden. Die verfügbaren Befehle können je nach Dateityp ändern.  
  
- **Des aktiven Fensters** das letzte aktive Dokumentfenster den Benutzerkontext für die Benutzeroberfläche (UI) für tastenbindungen festgelegt. Ein Toolfenster, das eine Tabelle von Schlüssel-Bindung verfügt, die den internen Webbrowser ähnelt jedoch festlegen auch den UI-Kontext. Jede Registerkarte hat mit mehreren Registerkarten Dokumentfenster wie z. B. der HTML-Editor einen anderen Befehlskontext-GUID. Nach dem Registrieren eines Toolfensters ist es immer verfügbar, auf die **Ansicht** Menü.  
  
- **UI-Kontext** Benutzeroberfläche-Kontexte werden durch die Werte der identifiziert die <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Klasse, z. B. <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> , wenn die Projektmappe erstellt wird, oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> Wenn der Debugger aktiv ist. Mehrere UI-Kontext können gleichzeitig aktiv sein.  
  
## <a name="defining-custom-context-guids"></a>Definieren von benutzerdefinierten Kontext-GUIDs  
 Wenn einen entsprechenden Befehl-Kontext, den GUID noch nicht definiert ist, können Sie eine solche im VSPackage definieren, und klicken Sie dann Programmieren zu aktiven oder inaktiven nach Bedarf, um die Sichtbarkeit Ihrer Befehle zu steuern.  
  
1. Registrieren Sie die Kontext-GUIDs durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode.  
  
2. Rufen Sie den Status der Kontext-GUID durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode.  
  
3. Aktivieren Sie das Kontext-GUIDs und deaktivieren durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode.  
  
    > [!CAUTION]
    >  Stellen Sie sicher, dass Ihr VSPackage keine vorhandenen Kontext GUIDs auswirkt, da es sich bei anderen VSPackages möglicherweise von ihnen abhängig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
