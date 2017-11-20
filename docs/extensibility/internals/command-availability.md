---
title: "Befehl Verfügbarkeit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecdbdc3074ad6dc80a8bd713c46303ba3cca628c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="command-availability"></a>Befehl-Verfügbarkeit
Der Visual Studio-Kontext wird bestimmt, welche Befehle verfügbar sind. Den Kontext kann ändern, je nach dem aktuellen Projekt, den aktuellen Editor, die VSPackages, die geladen werden und andere Aspekte der integrierten Entwicklungsumgebung (IDE).  
  
## <a name="command-contexts"></a>Befehl Kontexte  
 Der folgende Befehl Kontexte sind die häufigsten.  
  
-   **IDE** Befehle, die von der IDE bereitgestellt sind immer verfügbar.  
  
-   **VSPackage** VSPackages können definieren, wenn Befehle angezeigt oder ausgeblendet werden.  
  
-   **Projekt** Befehle nur für das aktuell ausgewählte Projekt angezeigt.  
  
-   **Editor** kann nur einer der Redakteure aktiv sein. Befehle aus dem aktiven Editor zur Verfügung. Ein Editor arbeitet eng mit einen Sprachdienst. Der Sprachdienst muss die Befehle im Kontext des zugehörigen Editors verarbeiten.  
  
-   **Dateityp** ein Editors kann mehr als eine Art von Datei laden. Die verfügbaren Befehle können je nach Dateityp ändern.  
  
-   **Aktives Fenster** die letzte aktive Fenster des Kontexts für die Benutzeroberfläche (UI) für tastenbindungen festgelegt. Ein Toolfenster mit einer Schlüssel-Bindung-Tabelle, die den internen Webbrowser ähnelt jedoch festlegen auch die Benutzeroberflächenkontext. Für Registerkarten Dokumentfenster z. B. den HTML-Editor hat jede Registerkarte einen anderen Befehl-Kontext GUID. Nachdem ein Toolfenster registriert ist, steht er immer auf die **Ansicht** Menü.  
  
-   **Benutzeroberflächenkontext** UI Kontexten prognostiziert nach den Werten der <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Klasse, zum Beispiel <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding> , wenn die Projektmappe erstellt wird, oder <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging> Wenn der Debugger aktiv ist. Mehrere UI-Kontexte können gleichzeitig aktiv sein.  
  
## <a name="defining-custom-context-guids"></a>Definieren von benutzerdefinierten Kontext-GUIDs  
 Wenn einen entsprechenden Befehl-Kontext, den GUID noch nicht definiert ist, können Sie in Ihrem VSPackage definieren und Programmieren Sie es als aktiv oder inaktiv nach Bedarf, um die Sichtbarkeit der Befehle zu steuern.  
  
1.  Registrieren von GUIDs Kontext durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode.  
  
2.  Der Zustand eines Kontexts GUID abzurufen, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode.  
  
3.  Aktivieren und deaktivieren Kontext-GUIDs, durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode.  
  
    > [!CAUTION]
    >  Stellen Sie sicher, dass Ihr VSPackage da anderen VSPackages davon abhängig sind, möglicherweise keine vorhandenen Kontext GUIDs auswirkt.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)