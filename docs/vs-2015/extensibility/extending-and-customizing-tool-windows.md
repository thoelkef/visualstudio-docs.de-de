---
title: Erweitern und Anpassen von Tool Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90ba7833a48647043fcb9b6d8ca9095be7cabef0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510603"
---
# <a name="extending-and-customizing-tool-windows"></a>Erweitern und Anpassen von Toolfenstern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [erweitern und Anpassen von Tool Windows](https://docs.microsoft.com/visualstudio/extensibility/extending-and-customizing-tool-windows).  
  
Visual Studio bietet verschiedene Arten von Windows, z. B. Toolfenster Dokumentfenster und Dialogfeldern. Andere Fenster wie das Fenster "Eigenschaften", das Fenster "Ausgabe" und das Fenster "Aufgabenliste", sind die Typen von Toolfenstern.  
  
## <a name="tool-windows"></a>Toolfenster  
 Visual Studio-Toolfenster sind in der Regel schreibgeschützte Fenster, die nicht dateibasiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Vorgehensweise: erstellen ein einfachen Toolfensters, finden Sie unter [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
 Um ein Toolfenster in Visual Studio zu registrieren, finden Sie unter [Registrieren eines Toolfensters](../extensibility/registering-a-tool-window.md).  
  
 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie ein Einzelinstanz-Toolfenster schließen, ändert sich nur seine Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Finden Sie unter [Erstellen eines Toolfensters mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md) für Weitere Informationen.  
  
 Toolfenster können werden *dynamische*, was bedeutet, dass sie angezeigt werden, wenn ihr zugehörige Benutzeroberflächenkontext gilt. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [Öffnen eines dynamischen Toolfensters](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.  
  
 Toolfensterbereiche können WPF-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können außer Kraft setzen der <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> Eigenschaft, um das Handle des gehosteten Steuerelements zurückzugeben.  
  
 Toolfenster können Sie zahlreiche unterschiedliche Features hinzufügen. Sie können z. B. eine Symbolleiste hinzufügen: [ein Toolfenster eine Symbolleiste hinzugefügt](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder ein Kontextmenü: [Hinzufügen eines Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Steuerelement für die Suche, die Ihnen ermöglicht, Elemente in das Toolfenster zu suchen, hinzufügen: [Hinzufügen der Suche zu einem Toolfenster](../extensibility/adding-search-to-a-tool-window.md).  
  
 Sie können Ereignisse abonnieren, Tool-Fenster: [Abonnieren eines Ereignisses](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Erweitern Sie vorhandene Tool Windows  
 Sie können Informationen über das Toolfenster hinzufügen, um ein neues **Optionen** Seite und eine neue Einstellung für die **Eigenschaften** Seite, das Schreiben auf die **Aufgabenliste** und **Ausgabe**  Windows. Weitere Informationen finden Sie unter [erweitern die Eigenschaften, Aufgabenliste, Ausgabe und Optionen für Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) und [erweitern die Eigenschaften, Aufgabenliste, Ausgabe und Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modale Dialogfelder  
 In Visual Studio-Erweiterung sollten Sie modale Dialogfelder erstellen, durch das Ableiten von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, sodass Sie sie und den Rest der Benutzeroberfläche zu steuern. Weitere Informationen finden Sie unter . [Erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)

