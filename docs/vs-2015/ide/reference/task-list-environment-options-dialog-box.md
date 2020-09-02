---
title: Aufgabenliste, Umgebung, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650962"
---
# <a name="task-list-environment-options-dialog-box"></a>Aufgabenliste, Umgebung, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Auf der Seite „Optionen“ können Sie die Kommentartoken hinzufügen, löschen und ändern, mit denen die Erinnerungen für **Aufgabenliste** generiert werden. Wählen Sie zum Anzeigen dieser Einstellungen **Optionen** aus dem Menü **Extras**, erweitern Sie den Ordner **Umgebung**, und wählen Sie **Aufgabenliste**.

## <a name="task-list-options"></a>Aufgabenlistenoptionen
 Löschen von Aufgaben bestätigen Wenn diese Option ausgewählt ist, wird jedes Mal ein Meldungs Feld angezeigt, wenn eine Benutzer Aufgabe aus dem **Aufgabenliste**gelöscht wird, sodass Sie den Löschvorgang bestätigen können. Diese Option ist standardmäßig ausgewählt.

> [!NOTE]
> Verwenden Sie zum Löschen eines Aufgabenkommentars den Link, um nach dem Kommentar zu suchen, und entfernen Sie ihn dann aus dem Code.

 Dateinamen nur anzeigen, wenn diese Option ausgewählt ist, werden in der Spalte **Datei** der **Aufgabenliste** nur die Namen der zu bearbeitenden Dateien angezeigt, nicht die vollständigen Pfade.

## <a name="tokens"></a>Token
 Wenn Sie einen Kommentar in den Code einfügen, dessen Text mit einem Token aus der **Tokenliste** beginnt, wird in der **Aufgabenliste** der Kommentar als neuer Eintrag angezeigt, wenn die Datei zur Bearbeitung geöffnet ist. Klicken Sie auf diesen Eintrag der **Aufgabenliste**, um direkt zur Kommentarzeile im Code zu springen. Weitere Informationen finden Sie unter [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md).

 Tokenliste zeigt eine Liste von Token an und ermöglicht das Hinzufügen oder Entfernen von benutzerdefinierten Token. In Visual C# und Visual C++ wird die Groß-/Kleinschreibung von Kommentartoken berücksichtigt, in Visual Basic jedoch nicht.

> [!NOTE]
> Wenn Sie das gewünschte Token nicht exakt so eingeben, wie es in der **Tokenliste** aufgeführt ist, wird in der **Aufgabenliste** keine Kommentaraufgabe angezeigt.

 Priorität legt die Priorität von Tasks fest, die das ausgewählte Token verwenden. Aufgabenkommentaren, die mit diesem Token beginnen, wird in der **Aufgabenliste** automatisch die festgelegte Priorität zugewiesen.

 Name geben Sie die Token-Zeichenfolge ein. Dadurch wird die Schaltfläche **Hinzufügen** aktiviert. Durch Klicken auf **Hinzufügen** wird diese Zeichenfolge in die **Tokenliste** eingeschlossen, und in der **Aufgabenliste** werden Kommentare angezeigt, die mit diesem Namen beginnen.

 Hinzufügen aktiviert, wenn Sie einen neuen **Namen**eingeben. Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte eine neue Tokenzeichenfolge hinzuzufügen.

 Löschen klicken Sie hierauf, um das ausgewählte Token aus der **Tokenliste**zu löschen. Das Standardkommentartoken kann nicht gelöscht werden.

 Ändern klicken Sie hier, um mithilfe der in den Feldern **Name** und **Priorität** eingegebenen Werteänderungen an einem vorhandenen Token vorzunehmen.

> [!NOTE]
> Sie können das Standardkommentartoken weder umbenennen noch löschen, jedoch die Priorität dieses Tokens ändern.

## <a name="see-also"></a>Weitere Informationen
 [Verwenden des Aufgabenliste](../../ide/using-the-task-list.md) [Festlegen von Lesezeichen im](../../ide/setting-bookmarks-in-code.md) [Dialog Feld "Code Umgebungsoptionen](../../ide/reference/environment-options-dialog-box.md) "
