---
title: Erweitern und Anpassen von Toolfenstern | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef4f656ed7b7ab7facbcfb470fca98327276cce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129234"
---
# <a name="extending-and-customizing-tool-windows"></a>Erweitern und Anpassen von Toolfenstern
Visual Studio stellt verschiedene Typen von Windows, z. B. Toolfenster Dokumentfenster und Dialogfeldern bereit. Andere Fenster z. B. das Eigenschaftenfenster, Fenster "Ausgabe" und das Fenster "Aufgabenliste" sind die Typen der Toolfenster.  
  
## <a name="tool-windows"></a>Toolfenster  
 Visual Studio-Toolfenster sind in der Regel schreibgeschützt Fenstern, die nicht dateibasiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Gewusst wie: Erstellen eines einfachen Toolfensters feststellen zu können, finden Sie unter [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
 Um ein Toolfenster in Visual Studio zu registrieren, finden Sie unter [registrieren ein Toolfenster](../extensibility/registering-a-tool-window.md).  
  
 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie ein Einzelinstanz-Toolfenster schließen, ändert sich nur seine Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Finden Sie unter [erstellen ein Toolfenster mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md) für Weitere Informationen.  
  
 Toolfenster können werden *dynamische*, was bedeutet, dass sie angezeigt werden, wenn ihr zugehörige Benutzeroberflächenkontext gilt. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [Öffnen eines Toolfensters dynamische](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.  
  
 Toolfensterbereiche können WPF-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können außer Kraft setzen die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> Eigenschaft, um das Handle des gehosteten Steuerelements zurückzugeben.  
  
 Toolfenster können Sie zahlreiche unterschiedliche Features hinzufügen. Sie können z. B. eine Symbolleiste hinzufügen: [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder ein Kontextmenü: [Hinzufügen eines Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Steuerelement für die Suche, die Ihnen ermöglicht, eine Suche in Ihr Toolfenster Elemente hinzufügen: [Suche hinzufügen, um ein Toolfenster](../extensibility/adding-search-to-a-tool-window.md).  
  
 Sie können Ereignisse abonnieren, Tool-Fenster: [Abonnieren eines Ereignisses](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Erweitern von vorhandenen Toolfenstern  
 Sie können Informationen über das Toolfenster hinzufügen, um ein neues **Optionen** Seiten- und eine neue Einstellung für die **Eigenschaften** Seite, das Schreiben auf die **Aufgabenliste** und **Ausgabe**  Windows. Weitere Informationen finden Sie unter [erweitern die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) und [erweitern die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modale Dialogfelder  
 In einer Visual Studio-Erweiterung sollten Sie modale Dialogfelder erstellen, indem Sie daraus ableiten <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, sodass Sie sie und den Rest der Benutzeroberfläche steuern. Weitere Informationen finden Sie unter . [Erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)