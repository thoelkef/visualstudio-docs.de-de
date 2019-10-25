---
title: Aufgabenliste, Umgebung, Dialogfeld "Optionen"
ms.date: 03/28/2019
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2d0ba45ffea940ddb57a6da1e6df55e3da8867b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644857"
---
# <a name="options-dialog-box-environment--task-list"></a>Dialogfeld „Optionen“: Umgebung \> Aufgabenliste

Auf der Seite „Optionen“ können Sie die Kommentartoken hinzufügen, löschen und ändern, mit denen die Erinnerungen für **Aufgabenliste** generiert werden. Wählen Sie zum Anzeigen dieser Einstellungen **Optionen** aus dem Menü **Extras**, erweitern Sie den Ordner **Umgebung**, und wählen Sie **Aufgabenliste**.

## <a name="task-list-tokens"></a>Aufgabenlistentoken

Wenn Sie einen Kommentar in den Code einfügen, dessen Text mit einem Token aus der **Tokenliste** beginnt, wird in der **Aufgabenliste** der Kommentar als neuer Eintrag angezeigt, wenn die Datei zur Bearbeitung geöffnet ist. Klicken Sie auf einen Eintrag in der **Aufgabenliste**, um direkt zur Kommentarzeile im Code zu springen. Weitere Informationen finden Sie unter [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md).

Tokenliste\
Zeigt eine Liste mit Token an und ermöglicht es Ihnen, benutzerdefinierte Token hinzuzufügen oder zu entfernen. In C# und C++ wird die Groß-/Kleinschreibung von Kommentartoken berücksichtigt, in Visual Basic jedoch nicht.

> [!NOTE]
> Wenn Sie das gewünschte Token nicht exakt so eingeben, wie es in der Tokenliste aufgeführt ist, wird in der **Aufgabenliste** keine Kommentaraufgabe angezeigt.

Priorität\
Legt die Priorität von Aufgaben fest, die das ausgewählte Token verwenden (niedrig, normal, hoch). Aufgabenkommentaren, die mit diesem Token beginnen, wird in der **Aufgabenliste** automatisch die festgelegte Priorität zugewiesen.

Name\
Geben Sie hier die Tokenzeichenfolge ein, und klicken Sie dann auf **Hinzufügen**, um die Zeichenfolge der Tokenliste hinzuzufügen.

Hinzufügen\
Wird aktiviert, wenn Sie einen neuen **Namen** eingeben. Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte eine neue Tokenzeichenfolge hinzuzufügen.

Löschen\
Klicken Sie auf diese Schaltfläche, wenn Sie das ausgewählte Token aus der Tokenliste entfernen möchten. Das Standardkommentartoken kann nicht gelöscht werden.

Ändern\
Klicken Sie auf diese Schaltfläche, um unter Verwendung der in die Felder **Name** und **Priorität** eingegebenen Werte Änderungen an einem vorhandenen Token vorzunehmen.

> [!NOTE]
> Sie können das Standardkommentartoken weder umbenennen noch löschen, jedoch die Priorität dieses Tokens ändern.

## <a name="see-also"></a>Siehe auch

- [Verwenden der Aufgabenliste](../../ide/using-the-task-list.md)
- [Festlegen von Textmarken im Code](../../ide/setting-bookmarks-in-code.md)