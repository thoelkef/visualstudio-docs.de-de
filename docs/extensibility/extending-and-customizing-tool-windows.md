---
title: "Erweitern und Anpassen von Toolfenstern | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Benutzeroberflächen essentials"
  - "Toolfenster, standard"
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Erweitern und Anpassen von Toolfenstern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio bietet verschiedene Arten von Windows, z. B. Toolfenster Dokumentfenster und Dialogfeldern. Andere Fenster wie im Eigenschaftenfenster, im Ausgabefenster und der Aufgabenliste sind Typen von Toolfenstern.  
  
## Toolfenster  
 Visual Studio\-Toolfenster sind normalerweise schreibgeschützt Windows, die nicht dateibasierte sind. In diesem unterscheiden sich jedoch von Dokumentfenster, die Dateien im schreibgeschützten Modus angezeigt. Die **Toolbox**, **Projektmappen\-Explorer**, **Eigenschaften** Fenster und **Webbrowser** sind Beispiele für Toolfenster.  
  
 Um herauszufinden, wie ein einfaches Tool\-Fenster zu erstellen, finden Sie unter [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
 Um ein Toolfenster in Visual Studio zu registrieren, finden Sie unter [Registrieren ein Toolfenster](../extensibility/registering-a-tool-window.md).  
  
 Toolfenster Einzel\-Instanz werden in der Standardeinstellung bedeutet, dass nur eine Instanz des Toolfensters kann offen sein zu einem Zeitpunkt. Nachdem eine Einzelinstanz\-Toolfenster geöffnet wird, bleibt es geöffnet, bis die IDE geschlossen wird. Beim Schließen eines Toolfensters Einzel\-Instanz ändert nur die Sichtbarkeit. Sie können auch mit mehreren Instanzen Toolfenster erstellen, dass mehrere Instanzen des Fenster gleichzeitig geöffnet sein können. Weitere Informationen finden Sie unter [Erstellen eines Toolfensters mit mehreren Instanzen](../extensibility/creating-a-multi-instance-tool-window.md).  
  
 Toolfenster können werden *dynamische*, was bedeutet, dass sie angezeigt werden, wenn ihre verwandten Benutzeroberflächenkontext gilt. Die Verwendung der automatischen Sichtbarkeit kann die Übersichtlichkeit in der IDE aus. Weitere Informationen finden Sie unter [Öffnen ein dynamisches Tool\-Fenster](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Toolfenster können angedockt, Gleitkomma oder im Dokumentrahmen im Registerformat werden. Die Toolfenster, Rahmen wird von der IDE bereitgestellt und wird verwendet, um die Größe, Position, andockzustand und anderen permanenten Eigenschaften steuern. Die Tool\-Fensterbereich zeigt den Inhalt. Die Standardgröße und der Standardposition gelten nur bei im Toolfenster erstmalig geöffnet wird. Danach wird der Fensterzustand Tool beibehalten.  
  
 Fensterbereiche Tool können Hosten von WPF\-Benutzersteuerelemente und Symbolleisten unterstützen. Sie können außer Kraft setzen die <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> Eigenschaft, um das Handle des gehosteten Steuerelements zurück.  
  
 Toolfenster können Sie zahlreiche unterschiedliche Features hinzufügen. Sie können z. B. eine Symbolleiste hinzufügen: [Ein Toolfenster hinzugefügt eine Symbolleiste](../extensibility/adding-a-toolbar-to-a-tool-window.md) oder ein Kontextmenü: [Hinzufügen eines Kontextmenüs in einem Toolfenster](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Sie können ein Steuerelement für die Suche, die Sie Elemente in das Toolfenster suchen kann hinzufügen: [Hinzufügen von Suchfunktionen zu einem Toolfenster](../extensibility/adding-search-to-a-tool-window.md).  
  
 Sie können Fensterereignisse abonnieren: [Abonnieren eines Ereignisses](../extensibility/subscribing-to-an-event.md).  
  
## Erweitern Sie vorhandene Toolfenster  
 Sie können Informationen über das Toolfenster hinzufügen, um ein neues **Optionen** Seite und eine neue Einstellung für die **Eigenschaften** Seite, das Schreiben auf die **Aufgabenliste** und **Ausgabe** Windows. Weitere Informationen finden Sie unter [Erweitern Sie die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) und [Erweitern Sie die Eigenschaften, die Aufgabenliste, die Ausgabe und die Optionen Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## Modale Dialogfelder  
 Visual Studio\-Erweiterung erstellen Sie in modalen Dialogfeldern durch Ableitung von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, wodurch sie und den Rest der Benutzeroberfläche zu steuern. Weitere Informationen finden Sie unter.[Erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## Siehe auch  
 [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)