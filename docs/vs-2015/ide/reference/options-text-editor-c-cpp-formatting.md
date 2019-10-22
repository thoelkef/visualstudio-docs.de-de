---
title: Optionen, Text-Editor, C/C++, Formatierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662331"
---
# <a name="options-text-editor-cc-formatting"></a>Optionen, Text-Editor, C/C++, Formatierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ermöglicht es Ihnen, das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.

 Um diese Seite zu öffnen, klicken Sie im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie den **Text-Editor** und **C/C++** und klicken dann auf **Formatieren**.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>C/C++-Optionen
 **Automatische Quick Infos aktivieren** Aktiviert oder deaktiviert die IntelliSense-Funktion Quick Info.

## <a name="inactive-code"></a>Inaktiver Code
 **Inaktive Code Blöcke anzeigen** Code, der aufgrund von `#ifdef` Deklarationen inaktiv ist, wird unterschiedlich eingefärbt, damit Sie ihn leichter identifizieren können.

 **Inaktive Code Deckkraft deaktivieren** Inaktiver Code kann mit Color anstelle der Transparenz identifiziert werden.

 **Inaktive Code Deckkraft in Prozent** Der Grad der Deckkraft für inaktive Code Blöcke kann angepasst werden.

## <a name="indentation"></a>Indentation
 Geschweifte **Klammern** einziehen Sie können konfigurieren, wie geschweifte Klammern ausgerichtet werden, wenn Sie die EINGABETASTE drücken, nachdem Sie einen Codeblock begonnen haben, z. b. eine Funktion oder eine `for` Schleife. Die geschweiften Klammern können entweder am ersten Zeichen des Codeblocks ausgerichtet oder eingezogen sein.

 **Automatischer Einzug auf Registerkarte** Sie können konfigurieren, was auf der aktuellen Codezeile geschieht, wenn Sie die Tab-Taste drücken. Entweder wird die Zeile eingezogen oder ein Tabulator eingefügt.

## <a name="miscellaneous"></a>Verschiedenes
 **Listet die Kommentare im Aufgabenliste Fenster auf** . Der Editor kann geöffnete Quelldateien nach vordefinierten Wörtern in den Kommentaren durchsuchen. Er erstellt einen Eintrag im Fenster **Aufgabenliste** für beliebige Schlüsselwörter, die gefunden werden.

 **Übereinstimmende Token markieren** Wenn sich der Cursor neben einer geschweifter Klammer befindet, kann der Editor die entsprechende geschweifter Klammer hervorheben, damit Sie den enthaltenen Code leichter sehen können.

## <a name="outlining"></a>Gliedern
 Gliederungs **Modus beim Öffnen von Dateien eingeben** Wenn Sie eine Datei in den Text-Editor verschieben, können Sie die Gliederungs Funktion aktivieren. Weitere Informationen finden Sie unter [Gliedern](../../ide/outlining.md). Wenn diese Option ausgewählt ist, wird die Gliederungsfunktion beim Öffnen einer Datei aktiviert.

 **Automatisches Gliedern von #pragma Regions Blöcken** Wenn diese Option ausgewählt ist, wird die automatische Gliederung für [pragma-Anweisungen](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) aktiviert. Damit können Sie Pragmabereichsblocks im gegliederten Modus erweitern oder reduzieren.

 **Automatische Gliederung von Anweisungs Blöcken** Wenn diese Option ausgewählt ist, wird die automatische Gliederung für die folgenden Anweisungs Konstrukte aktiviert:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [switch-Anweisung (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while-Anweisung (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Siehe auch
 [Allgemein, Umgebung, Dialog Feld "Optionen](../../ide/reference/general-environment-options-dialog-box.md) " unter [Verwendung von IntelliSense](../../ide/using-intellisense.md)
