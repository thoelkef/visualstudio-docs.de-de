---
title: "Aufgabenliste, Umgebung, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.Task_List"
  - "VS.ToolsOptionsPag.Environment.Task_List"
  - "VS.ToolsOptionsPages.Environment.TaskList"
  - "VS.Environment.Task List"
helpviewer_keywords: 
  - "Tokenliste"
  - "tokens"
  - "Symbole, in der Aufgabenliste"
  - "Aufgabenliste, Anpassen der Umgebung"
  - "Optionen (Dialogfeld), Aufgabenliste (Umgebung)"
  - "Ausrufezeichen"
  - "Kommentare, Kommentieren von Aufgaben in der Aufgabenliste"
  - "Token, und die Aufgabenliste"
  - "Aufgabenliste, Kommentieren von Aufgaben"
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Aufgabenliste, Umgebung, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Auf der Seite „Optionen“ können Sie die Kommentartoken hinzufügen, löschen und ändern, mit denen die Erinnerungen für **Aufgabenliste** generiert werden.  Wählen Sie zum Anzeigen dieser Einstellungen **Optionen** aus dem Menü **Extras**, erweitern Sie den Ordner **Umgebung**, und wählen Sie **Aufgabenliste**.  
  
## Aufgabenlistenoptionen  
 Löschen von Aufgaben bestätigen  
 Bei Auswahl dieser Option wird ein Meldungsfeld angezeigt, wenn eine Benutzeraufgabe aus der **Aufgabenliste** gelöscht wird, damit Sie den Löschvorgang bestätigen können.  Diese Option ist standardmäßig ausgewählt.  
  
> [!NOTE]
>  Verwenden Sie zum Löschen eines Aufgabenkommentars den Link, um nach dem Kommentar zu suchen, und entfernen Sie ihn dann aus dem Code.  
  
 Nur Dateinamen anzeigen  
 Bei Auswahl dieser Option werden in der Spalte **Datei** der **Aufgabenliste** nur die Namen der zu bearbeitenden Dateien angezeigt, und nicht die vollständigen Pfade.  
  
## Token  
 Wenn Sie einen Kommentar in den Code einfügen, dessen Text mit einem Token aus der **Tokenliste** beginnt, wird in der **Aufgabenliste** der Kommentar als neuer Eintrag angezeigt, wenn die Datei zur Bearbeitung geöffnet ist.  Klicken Sie auf diesen Eintrag der **Aufgabenliste**, um direkt zur Kommentarzeile im Code zu springen.  Weitere Informationen finden Sie unter [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md).  
  
 Tokenliste  
 Zeigt eine Liste mit Token an und ermöglicht es Ihnen, benutzerdefinierte Token hinzuzufügen oder zu entfernen.  In Visual C\# und Visual C\+\+ wird die Groß\-\/Kleinschreibung von Kommentartoken berücksichtigt, in Visual Basic jedoch nicht.  
  
> [!NOTE]
>  Wenn Sie das gewünschte Token nicht exakt so eingeben, wie es in der **Tokenliste** aufgeführt ist, wird in der **Aufgabenliste** keine Kommentaraufgabe angezeigt.  
  
 Priorität  
 Legt die Priorität von Aufgaben fest, die das ausgewählte Token verwenden.  Aufgabenkommentaren, die mit diesem Token beginnen, wird in der **Aufgabenliste** automatisch die festgelegte Priorität zugewiesen.  
  
 Name  
 Geben Sie die Tokenzeichenfolge ein.  Dadurch wird die Schaltfläche **Hinzufügen** aktiviert.  Durch Klicken auf **Hinzufügen** wird diese Zeichenfolge in die **Tokenliste** eingeschlossen, und in der **Aufgabenliste** werden Kommentare angezeigt, die mit diesem Namen beginnen.  
  
 Hinzufügen  
 Wird aktiviert, wenn Sie einen neuen **Namen** eingeben.  Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte eine neue Tokenzeichenfolge hinzuzufügen.  
  
 Löschen  
 Klicken Sie auf diese Schaltfläche, wenn Sie das ausgewählte Token aus der **Tokenliste** entfernen möchten.  Das Standardkommentartoken kann nicht gelöscht werden.  
  
 Änderung  
 Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte Änderungen an einem vorhandenen Token vorzunehmen.  
  
> [!NOTE]
>  Sie können das Standardkommentartoken weder umbenennen noch löschen, jedoch die Priorität dieses Tokens ändern.  
  
## Siehe auch  
 [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md)   
 [Festlegen von Lesezeichen im Code](../../ide/setting-bookmarks-in-code.md)   
 [Dialogfeld "Umgebungsoptionen"](../../ide/reference/environment-options-dialog-box.md)