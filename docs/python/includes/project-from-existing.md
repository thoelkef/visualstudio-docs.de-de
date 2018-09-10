---
ms.topic: include
ms.openlocfilehash: 47c390fbc7a6f84c25d4bde0317985bd149cae2f
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252491"
---
1. Starten Sie Visual Studio, und klicken Sie auf **Datei** > **Neu** > **Projekt**.

1. Suchen Sie im Dialogfeld **Neues Projekt** nach „Python“, wählen Sie die Vorlage **Aus vorhandenem Python-Code** aus, legen Sie für das Projekt einen Namen und einen Speicherort fest, und klicken Sie anschließend auf **OK**.

1. Legen Sie im Assistenten, der angezeigt wird, den Pfad zu Ihrem vorhandenen Code und einen Filter für Dateitypen fest, geben Sie Suchpfade an, die das Projekt benötigt, und klicken Sie auf **Weiter**. Wenn Sie nicht wissen, was Suchpfade sind, lassen Sie das Feld leer.

    ![Neues Projekt aus vorhandenem Code – Schritt 1](../media/projects-from-existing-1.png)

1. Wählen Sie im nächsten Dialogfeld die Startdatei für Ihr Projekt aus, und klicken Sie auf **Weiter**. (Falsch gewünscht, wählen Sie eine Umgebung aus. Akzeptieren Sie andernfalls die Standardwerte.) Beachten Sie, dass das Dialogfeld nur Dateien im Stammordner anzeigt. Wenn die gewünschte Datei sich in einem Unterordner befindet, und geben Sie keine Startdatei an, sondern legen Sie sie später im **Projektmappen-Explorer** fest (siehe unten).

    ![Neues Projekt aus vorhandenem Code – Schritt 2](../media/projects-from-existing-2.png)

1. Wählen Sie den Speicherort aus, an dem die Projektdatei gespeichert werden soll (eine *PYPROJ*-Datei auf dem Datenträger). Sie können auch die automatische Erkennung virtueller Umgebungen einbeziehen und das Projekt für andere Webframeworks anpassen (falls zutreffend). Wenn Sie sich bei diesen Optionen nicht sicher sind, verwenden Sie die Standardwerte.

    ![Neues Projekt aus vorhandenem Code – Schritt 3](../media/projects-from-existing-3.png)

1. Klicken Sie auf **Fertig stellen**. Visual Studio erstellt nun das Projekt und öffnet es im **Projektmappen-Explorer**. Wenn Sie die *PYPROJ*-Datei an eine andere Stelle verschieben möchten, wählen Sie sie im **Projektmappen-Explorer** aus, und klicken Sie auf **Datei** > **Speichern unter**. Diese Aktion aktualisiert Dateiverweise im Projekt, verschiebt aber keine Codedateien.

1. Wenn Sie eine andere Startdatei festlegen möchten, suchen Sie die Datei im **Projektmappen-Explorer**, führen Sie einen Rechtsklick aus, und klicken Sie anschließend auf **Set as Startup File** (Als Startdatei festlegen).