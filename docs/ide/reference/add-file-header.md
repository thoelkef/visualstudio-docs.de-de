---
title: Hinzufügen von Dateiheadern
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44c3b64d9fb8944a578d054b7d98d4bf39bde3bc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810375"
---
# <a name="add-file-header"></a>Hinzufügen von Dateiheadern

Diese Codegenerierung gilt für:

- C#

- Visual Basic

**Beschreibung:** Hinzufügen von Dateiheadern zu vorhandenen Dateien, Projekten und Projektmappen mithilfe einer [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)-Datei.

**Hintergrund:** Sie möchten Dateien, Projekten und Projektmappen problemlos einen Dateiheader hinzufügen.

**Vorteile**: Ihr Team verlangt, dass Sie einen Dateiheader mit Informationen zum Copyright einschließen. 

## <a name="how-to"></a>Vorgehensweise

1. Fügen Sie einem Projekt oder einer Projektmappe eine [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)-Datei hinzu, falls Sie noch keine haben.

2. Fügen Sie Ihrer EditorConfig-Datei die folgende Regel hinzu: *file_header_template*.

3. Legen Sie den Wert der Regel so fest, dass er dem gewünschten Headertext entspricht. Sie können `{fileName}` als Platzhalter für den Dateinamen verwenden.

    ![Headerregel in einer EditorConfig-Datei](media/add-file-header-rule.png)

    > [!NOTE]
    > In einer EditorConfig-Datei sind mehrere Zeilen explizit nicht möglich, weshalb Sie zum Einfügen neuer Zeilen das UNIX-Zeichen für Zeilenumbrüche verwenden müssen.

4. Platzieren Sie die Einfügemarke in der ersten Zeile einer beliebigen C#- oder Visual Basic-Datei.

5. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

6. Wählen Sie **Dateiheader hinzufügen** aus. 

    ![Headerregel in einer EditorConfig-Datei](media/add-file-header.png)

7. Um den Dateiheader für alle Dateien eines vorhandenen Projekts oder einer vorhandenen Projektmappe zu übernehmen, klicken Sie unter der Option **Alle Vorkommen korrigieren in** auf **Projekt** oder **Projektmappe**.

8. Das Dialogfeld **Alle Vorkommnisse korrigieren** wird mit einer Vorschau der Änderungen geöffnet.

    ![Dialogfeld „Alle Vorkommen korrigieren“](media/file-header-preview-changes.png)

8. Wählen Sie **Übernehmen** aus, um die Änderungen zu übernehmen.

## <a name="see-also"></a>Siehe auch

- [Codegenerierung](../code-generation-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)