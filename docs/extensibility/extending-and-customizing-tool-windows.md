---
title: Erweitern und Anpassen von Tool Windows | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0eafb5a95151d6c3a805ad4d51c847f2fbe269d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341141"
---
# <a name="extend-and-customize-tool-windows"></a>Erweitern und Anpassen von Toolfenstern
Visual Studio bietet verschiedene Arten von Windows, z. B. Toolfenster Dokumentfenster und Dialogfeldern. Andere Fenster z. B. die **Eigenschaften** Fenster die **Ausgabe** Fenster, und die **Aufgabenliste** Fenster gibt Typen von Toolfenstern.

## <a name="tool-windows"></a>Toolfenster
 Visual Studio-Toolfenster sind in der Regel schreibgeschützte Fenster, die nicht dateibasiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.

 Vorgehensweise: erstellen ein einfachen Toolfensters, finden Sie unter [hinzufügen ein Toolfensters](../extensibility/adding-a-tool-window.md).

 Um ein Toolfenster in Visual Studio zu registrieren, finden Sie unter [registrieren ein Toolfensters](../extensibility/registering-a-tool-window.md).

 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie ein Einzelinstanz-Toolfenster schließen, ändert sich nur seine Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Finden Sie unter [erstellen ein Toolfensters mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md) für Weitere Informationen.

 Toolfenster können werden *dynamische*, was bedeutet, dass sie angezeigt werden, wenn ihr zugehörige Benutzeroberflächenkontext gilt. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [öffnen Sie ein dynamisches Tool](../extensibility/opening-a-dynamic-tool-window.md).

 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.

 Toolfensterbereiche können WPF-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>-Eigenschaft außer Kraft setzen, um das Handle des gehosteten Steuerelements zurückzugeben.

 Toolfenster können Sie zahlreiche unterschiedliche Features hinzufügen. Beispielsweise können Sie eine Symbolleiste hinzufügen: [Hinzufügen einer Symbolleiste zu einem Toolfenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder ein Kontextmenü: [Hinzufügen ein Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Steuerelement für die Suche hinzufügen, die Sie Elemente in das Toolfenster suchen können: [Hinzufügen der Suche zu einem Toolfenster](../extensibility/adding-search-to-a-tool-window.md).

 Sie können Tool Window-Ereignissen abonnieren: [Abonnieren eines Ereignisses](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Erweitern Sie vorhandene Toolfenster
 Sie können Informationen über das Toolfenster hinzufügen, um ein neues **Optionen** Seite und eine neue Einstellung für die **Eigenschaften** Seite, das Schreiben auf die **Aufgabenliste** und **Ausgabe**  Windows. Weitere Informationen finden Sie unter [erweitern Sie die Eigenschaften "," Aufgabenliste "," Ausgabe "und" Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) und [erweitern Sie die Eigenschaften "," Aufgabenliste "," Ausgabe "und" Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modale Dialogfelder
 In Visual Studio-Erweiterung sollten Sie modale Dialogfelder erstellen, durch das Ableiten von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, sodass Sie sie und den Rest der Benutzeroberfläche zu steuern. Weitere Informationen finden Sie unter [erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Siehe auch
- [Erstellen Sie eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)