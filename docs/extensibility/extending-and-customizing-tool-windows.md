---
title: Erweiterungs- und Customizing-Tool Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711816"
---
# <a name="extend-and-customize-tool-windows"></a>Erweitern und Anpassen von Toolfenstern
Visual Studio bietet verschiedene Fenstertypen, z. B. Toolfenster, Dokumentfenster und Dialogfenster. Andere Fenster wie das **Eigenschaftenfenster,** das **Ausgabefenster** und das **Fenster Aufgabenliste** sind Arten von Toolfenstern.

## <a name="tool-windows"></a>Toolfenster
 Visual Studio-Toolfenster sind in der Regel schreibgeschützte Fenster, die nicht dateibasiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.

 Informationen zum Erstellen eines einfachen Toolfensters finden Sie unter [Hinzufügen eines Werkzeugfensters](../extensibility/adding-a-tool-window.md).

 Informationen zum Registrieren eines Toolfensters bei Visual Studio finden Sie unter [Registrieren eines Toolfensters](../extensibility/registering-a-tool-window.md).

 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie ein Werkzeugfenster mit einer Instanz schließen, ändert sich nur die Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Weitere Informationen finden Sie unter [Erstellen eines Toolfensters mit mehreren Instanzen.](../extensibility/creating-a-multi-instance-tool-window.md)

 Toolfenster können *dynamisch*sein, d. h., sie sind immer sichtbar, wenn der zugehörige UI-Kontext angewendet wird. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [Öffnen eines dynamischen Werkzeugfensters](../extensibility/opening-a-dynamic-tool-window.md).

 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.

 Toolfensterbereiche können WPF-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>-Eigenschaft außer Kraft setzen, um das Handle des gehosteten Steuerelements zurückzugeben.

 Sie können Den Toolfenstern viele verschiedene Features hinzufügen. Sie können z. B. eine Symbolleiste hinzufügen: [Hinzufügen einer Symbolleiste zu einem Toolfenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder einem Kontextmenü: [Hinzufügen eines Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Suchsteuerelement hinzufügen, mit dem Sie Elemente in Ihrem Toolfenster durchsuchen können: [Suchen zu einem Toolfenster hinzufügen](../extensibility/adding-search-to-a-tool-window.md).

 Sie können Toolfenster-Ereignisse abonnieren: [Abonnieren eines Ereignisses](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Erweitern vorhandener Toolfenster
 Sie können Informationen über Ihr Toolfenster zu einer neuen **Optionsseite** und eine neue Einstellung auf der **Seite Eigenschaften** hinzufügen, in die **Aufgabenliste** schreiben und **die Fenster Ausgabe ausgeben.** Weitere Informationen finden Sie unter [Erweitern der Fenster Eigenschaften, Aufgabenliste, Ausgabe und Optionen](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modale Dialogfelder
 In einer Visual Studio-Erweiterung sollten Sie modale <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>Dialogfelder erstellen, indem Sie sie von ableiten, wodurch Sie sie und den Rest der Benutzeroberfläche steuern können. Weitere Informationen finden Sie unter [Erstellen und Verwalten modaler Dialogfelder](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Erweitern von Projekten](../extensibility/extending-projects.md)
- [Erweitern von Lösungen](../extensibility/extending-solutions.md)
