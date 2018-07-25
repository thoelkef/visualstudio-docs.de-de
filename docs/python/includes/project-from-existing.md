---
ms.topic: include
ms.openlocfilehash: 37079cfaa1204cd8ce7a77e1e2f5aa91ea844ea5
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809417"
---
1. Starten Sie Visual Studio, und wählen Sie **Datei > Neu > Projekt** aus.

1. Suchen Sie im Dialogfeld **Neues Projekt** nach „Python“, wählen Sie die Vorlage „Aus vorhandenem Python-Code“ aus, legen Sie für das Projekt einen Namen und einen Speicherort fest, und klicken Sie anschließend auf **OK**.

1. Legen Sie im Assistenten, der angezeigt wird, den Pfad zu Ihrem vorhandenen Code und einen Filter für Dateitypen fest, geben Sie Suchpfade an, die das Projekt benötigt, und klicken Sie auf **Weiter**. Wenn Sie nicht wissen, was Suchpfade sind, lassen Sie das Feld leer.

    ![Neues Projekt aus vorhandenem Code – Schritt 1](../media/projects-from-existing-1.png)

1. Wählen Sie im nächsten Dialogfeld die Startdatei für Ihr Projekt aus, und klicken Sie auf **Weiter**. (Falsch gewünscht, wählen Sie eine Umgebung aus. Akzeptieren Sie andernfalls die Standardwerte.) Beachten Sie, dass das Dialogfeld nur Dateien im Stammordner anzeigt. Wenn die gewünschte Datei sich in einem Unterordner befindet, geben Sie keine Startdatei an, und legen Sie sie später im Projektmappen-Explorer fest (siehe unten).

    ![Neues Projekt aus vorhandenem Code – Schritt 2](../media/projects-from-existing-2.png)

1. Wählen Sie den Speicherort aus, an dem die Projektdatei gespeichert werden soll (eine `.pyproj`-Datei auf dem Datenträger). Sie können auch die automatische Erkennung virtueller Umgebungen einbeziehen und das Projekt für andere Webframeworks anpassen (falls zutreffend). Wenn Sie sich bei diesen Optionen nicht sicher sind, verwenden Sie die Standardwerte.

    ![Neues Projekt aus vorhandenem Code – Schritt 3](../media/projects-from-existing-3.png)

1. Klicken Sie auf **Fertig stellen**. Visual Studio erstellt nun das Projekt und öffnet es im Projektmappen-Explorer. Wenn Sie die `.pyproj`-Datei an eine andere Stelle verschieben möchten, wählen Sie sie im Projektmappen-Explorer aus, und wählen Sie **Datei > Speichern unter**. Diese Aktion aktualisiert Dateiverweise im Projekt, verschiebt aber keine Codedateien.

1. Um eine andere Startdatei festzulegen, suchen Sie die Datei im Projektmappen-Explorer, führen Sie einen Rechtsklick aus, und wählen Sie **Als Startdatei festlegen**.