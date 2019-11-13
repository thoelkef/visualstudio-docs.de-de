---
title: 'Vorgehensweise: Ausschließen von Projekten aus einem Build'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e72b072ad2cabab643d64f149a31b1b8dbb2a054
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713940"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Vorgehensweise: Ausschließen von Projekten aus einem Build

Sie können eine Projektmappe erstellen, ohne dafür alle darin enthaltenen Projekte erstellen zu müssen. Beispielsweise können Sie ein Projekt ausschließen, das die Erstellung unterbricht. Sie können dann das Projekt erstellen, nachdem Sie die Probleme ermittelt und behoben haben.

Sie können ein Projekt wie folgt ausschließen:

- Entfernen Sie es temporär aus der aktiven Projektmappenkonfiguration.

- Erstellen Sie eine Projektmappenkonfiguration, die das Projekt nicht enthält.

Weitere Informationen finden Sie unter [Grundlagen der Buildkonfigurationen](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>So entfernen Sie ein Projekt temporär aus der aktiven Projektmappenkonfiguration

1. Klicken Sie in der Menüleiste auf **Build** > **Konfigurations-Manager**.

2. Suchen Sie in der Tabelle **Projektkontexte** nach dem aus dem Build auszuschließenden Projekt.

3. Deaktivieren Sie in der Spalte **Build** das Kontrollkästchen für das Projekt.

4. Wählen Sie die Schaltfläche **Schließen** aus, und erstellen Sie die Projektmappe dann erneut.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>So erstellen Sie eine ein Projekt ausschließende Projektmappenkonfiguration

1. Klicken Sie in der Menüleiste auf **Build** > **Konfigurations-Manager**.

2. Wählen Sie in der Liste **Konfiguration der aktuellen Projektmappe** den Eintrag **\<Neu>** aus.

3. Geben Sie im Feld **Name** einen Namen für die Projektmappenkonfiguration ein.

4. Wählen Sie in der Liste **Copy settings from** (Einstellungen kopieren von) die Projektmappenkonfiguration aus, auf der die neue Konfiguration (beispielsweise **Debug**) basieren soll, und wählen Sie dann die Schaltfläche **OK** aus.

5. Deaktivieren Sie im Dialogfeld **Konfigurations-Manager** das Kontrollkästchen in der Spalte **Erstellen** für das Projekt, das Sie ausschließen möchten, und wählen Sie dann die Schaltfläche **Schließen** aus.

6. Stellen Sie auf der Symbolleiste **Standard** sicher, dass es sich bei der neuen Projektmappenkonfiguration um die aktive Konfiguration im Feld **Projektmappenkonfigurationen** handelt.

7. Wählen Sie in der Menüleiste **Erstellen** > **Projektmappe neu erstellen** aus.

## <a name="skipped-projects"></a>Übersprungene Projekte

Projekte können während des Builds übersprungen werden, weil Sie nicht auf dem neuesten Stand sind oder von der Konfiguration ausgeschlossen sind. Visual Studio verwendet MSBuild, um Ihre Projekte zu erstellen. MSBuild erstellt nur dann ein Ziel, wenn die Ausgabe älter ist als die Eingabe, wie durch die Zeitstempel der Datei festgelegt. Um einen erneuten Buildvorgang zu erzwingen, verwenden Sie den Befehl **Build** > **Projektmappe neu erstellen**.

Im Bereich **Build** des Fensters **Ausgabe** meldet Visual Studio die Anzahl der Projekte, die auf dem neuesten Stand sind, die Anzahl, die erfolgreich erstellt wurde, die Anzahl, die fehlgeschlagen ist, und die Anzahl, die übersprungen wurde. Die Anzahl übersprungener Projekte umfasst keine Projekte, die nicht erstellt wurden, weil sie auf dem neuesten Stand sind. Wenn Projekte von der aktiven Konfiguration ausgeschlossen werden, werden Sie während des Builds übersprungen. In der Buildausgabe wird eine Meldung angezeigt, die besagt, dass das Projekt übersprungen wird:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Wenn Sie herausfinden möchten, warum ein Projekt übersprungen wurde, notieren Sie sich die aktive Konfiguration (`Debug x86` im vorherigen Beispiel), und wählen Sie **Build** > **Konfigurations-Manager** aus. Sie können anzeigen oder ändern, welche Projekte für jede Konfiguration übersprungen werden, wie in diesem Artikel erläutert wird.

## <a name="see-also"></a>Siehe auch

- [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)
- [Vorgehensweise: Erstellen und Bearbeiten von Konfigurationen](../ide/how-to-create-and-edit-configurations.md)
- [Vorgehensweise: Gleichzeitiges Erstellen mehrerer Konfigurationen](../ide/how-to-build-multiple-configurations-simultaneously.md)