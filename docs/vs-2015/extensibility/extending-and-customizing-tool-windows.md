---
title: Erweitern und Anpassen von Tool Fenstern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204542"
---
# <a name="extending-and-customizing-tool-windows"></a>Erweitern und Anpassen von Toolfenstern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bietet verschiedene Arten von Fenstern, z. b. Tool Fenster, Dokument Fenster und Dialogfenster. Andere Fenster, wie z. b. die Eigenschaftenfenster, das Ausgabefenster und das Aufgabenliste Fenster, sind Typen von Tool Fenstern.  
  
## <a name="tool-windows"></a>Toolfenster  
 Visual Studio-Tool Fenster sind normalerweise schreibgeschützte Fenster, die nicht Datei basiert sind. Darin unterscheiden sie sich von Dokumentfenstern, in denen die Dateien im Modus mit Lese- und Schreibzugriff angezeigt werden. Die Fenster **Toolbox**, **Projektmappen-Explorer**, **Eigenschaften** und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Weitere Informationen zum Erstellen eines einfachen Tool Fensters finden Sie unter [Hinzufügen eines Tool Fensters](../extensibility/adding-a-tool-window.md).  
  
 Informationen zum Registrieren eines Tool Fensters in Visual Studio finden Sie unter [Registrieren eines Tool Fensters](../extensibility/registering-a-tool-window.md).  
  
 Toolfenster sind standardmäßig Einzelinstanzen, d. h. nur eine Instanz des Toolfensters kann jeweils geöffnet sein. Nachdem ein Einzelinstanz-Toolfenster geöffnet wurde, bleibt es geöffnet, bis die IDE geschlossen wird. Wenn Sie ein Einzel Instanz-Tool Fenster schließen, ändert sich nur die Sichtbarkeit. Sie können auch Toolfenster mit mehreren Instanzen erstellen, sodass mehrere Instanzen des Fensters gleichzeitig geöffnet sein können. Weitere Informationen finden Sie unter [Erstellen eines Tool Fensters mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md) .  
  
 Tool Fenster können *dynamisch*sein, was bedeutet, dass Sie sichtbar sind, wenn der zugehörige UI-Kontext angewendet wird. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit hinsichtlich der Fenster in der IDE verbessern. Weitere Informationen finden Sie unter [Öffnen eines dynamischen Tool Fensters](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Toolfenster können im Dokumentrahmen angedockt oder unverankert sein bzw. das Registerkartenformat aufweisen. Der Toolfensterrahmen wird von der IDE bereitgestellt und dazu verwendet, um das Format, die Position, den Andockzustand und andere permanente Eigenschaften zu steuern. Der Toolfensterbereich zeigt die Inhalte an. Das Standardformat und die Standardposition gelten nur beim ersten Öffnen des Toolfensters. Anschließend wird der Toolfensterzustand beibehalten.  
  
 Toolfensterbereiche können WPF-Benutzersteuerelemente hosten und Symbolleisten unterstützen. Sie können die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A>-Eigenschaft außer Kraft setzen, um das Handle des gehosteten Steuerelements zurückzugeben.  
  
 Sie können den Tool Fenstern viele verschiedene Funktionen hinzufügen. Sie können z. b. eine Symbolleiste hinzufügen: [Hinzufügen einer Symbolleiste zu einem Tool Fenster](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder einem Kontextmenü: [Hinzufügen eines Kontextmenüs in einem Tool Fenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Such Steuerelement hinzufügen, mit dem Sie Elemente in Ihrem Tool Fenster durchsuchen können: [Hinzufügen einer Suche zu einem Tool Fenster](../extensibility/adding-search-to-a-tool-window.md).  
  
 Sie können Tool Fenster Ereignisse abonnieren: abonnieren [eines Ereignisses](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Erweitern vorhandener Tool Fenster  
 Sie können Informationen über das Tool Fenster zu einer neuen **options** Seite und eine neue Einstellung auf der Seite **Eigenschaften** hinzufügen und in die Fenster **Aufgabenliste** und **Ausgabe** schreiben. Weitere Informationen finden Sie unter [Erweitern der Fenster Eigenschaften, Aufgabenliste, Ausgabe und Optionen](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) und [Erweitern der Fenster Eigenschaften, Aufgabenliste, Ausgabe und Optionen](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modale Dialog Felder  
 In einer Visual Studio-Erweiterung sollten Sie modale Dialogfelder erstellen, indem Sie Sie von ableiten <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , sodass Sie Sie und den Rest der Benutzeroberfläche steuern können. Weitere Informationen finden Sie unter . [Erstellen und Verwalten von modalen Dialog Feldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)
