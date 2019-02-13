---
title: Aufgabenliste, Umgebung, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bda16e5939f34cbea29eb92e08ee7325b49301b5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912169"
---
# <a name="task-list-environment-options-dialog-box"></a>Aufgabenliste, Umgebung, Dialogfeld "Optionen"

Auf der Seite „Optionen“ können Sie die Kommentartoken hinzufügen, löschen und ändern, mit denen die Erinnerungen für **Aufgabenliste** generiert werden. Wählen Sie zum Anzeigen dieser Einstellungen **Optionen** aus dem Menü **Extras**, erweitern Sie den Ordner **Umgebung**, und wählen Sie **Aufgabenliste**.

## <a name="task-list-options"></a>Aufgabenlistenoptionen
 Löschen von Aufgaben bestätigen

 Bei Auswahl dieser Option wird ein Meldungsfeld angezeigt, wenn eine Benutzeraufgabe aus der **Aufgabenliste** gelöscht wird, damit Sie den Löschvorgang bestätigen können. Diese Option ist standardmäßig ausgewählt.

> [!NOTE]
> Verwenden Sie zum Löschen eines Aufgabenkommentars den Link, um nach dem Kommentar zu suchen, und entfernen Sie ihn dann aus dem Code.


 Nur Dateinamen anzeigen

 Bei Auswahl dieser Option werden in der Spalte **Datei** der **Aufgabenliste** nur die Namen der zu bearbeitenden Dateien angezeigt, und nicht die vollständigen Pfade.

## <a name="tokens"></a>tokens
 Wenn Sie einen Kommentar in den Code einfügen, dessen Text mit einem Token aus der **Tokenliste** beginnt, wird in der **Aufgabenliste** der Kommentar als neuer Eintrag angezeigt, wenn die Datei zur Bearbeitung geöffnet ist. Klicken Sie auf diesen Eintrag der **Aufgabenliste**, um direkt zur Kommentarzeile im Code zu springen. Weitere Informationen finden Sie unter [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md).

 Tokenliste

 Zeigt eine Liste mit Token an und ermöglicht es Ihnen, benutzerdefinierte Token hinzuzufügen oder zu entfernen. In C# und Visual C++ wird die Groß-/Kleinschreibung von Kommentartoken berücksichtigt, in Visual Basic jedoch nicht.

> [!NOTE]
> Wenn Sie das gewünschte Token nicht exakt so eingeben, wie es in der **Tokenliste** aufgeführt ist, wird in der **Aufgabenliste** keine Kommentaraufgabe angezeigt.


 Priorität

 Legt die Priorität von Aufgaben fest, die das ausgewählte Token verwenden. Aufgabenkommentaren, die mit diesem Token beginnen, wird in der **Aufgabenliste** automatisch die festgelegte Priorität zugewiesen.

 name

 Geben Sie die Tokenzeichenfolge ein. Dadurch wird die Schaltfläche **Hinzufügen** aktiviert. Durch Klicken auf **Hinzufügen** wird diese Zeichenfolge in die **Tokenliste** eingeschlossen, und in der **Aufgabenliste** werden Kommentare angezeigt, die mit diesem Namen beginnen.

 Hinzufügen

 Wird aktiviert, wenn Sie einen neuen **Namen** eingeben. Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte eine neue Tokenzeichenfolge hinzuzufügen.

 Löschen

 Klicken Sie auf diese Schaltfläche, wenn Sie das ausgewählte Token aus der **Tokenliste** entfernen möchten. Das Standardkommentartoken kann nicht gelöscht werden.

 Änderung

 Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte Änderungen an einem vorhandenen Token vorzunehmen.

> [!NOTE]
> Sie können das Standardkommentartoken weder umbenennen noch löschen, jedoch die Priorität dieses Tokens ändern.


## <a name="see-also"></a>Siehe auch

- [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md)
- [Festlegen von Lesezeichen im Code](../../ide/setting-bookmarks-in-code.md)
- [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)