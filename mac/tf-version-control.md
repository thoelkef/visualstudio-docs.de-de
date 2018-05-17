---
title: TF-Versionskontrolle
description: Verbinden zu Team Foundation Server oder Visual Studio Team Services mit der Team Foundation-Versionskontrolle.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Verbinden zur Team Foundation-Versionskontrolle 

Visual Studio Team Services (VSTS) und Team Foundation Server (TFS) bieten zwei Modell der Versionskontrolle: Git, eine verteilte Versionskontrolle, sowie die Team Foundation-Versionskontrolle (TFVC), eine zentrale Versionskontrolle. Dieser Artikel enthält eine Übersicht und einen Ausgangspunkt für die Verwendung der Team Foundation-Versionskontrolle mit Visual Studio für Mac.

> [!NOTE]
> **Hinweis**: Bei der Unterstützung für die Team Foundation-Versionskontrolle handelt es sich derzeit um die Vorschauversion, und einige Funktionen funktionieren noch nicht vollständig. Weitere Änderungen werden folgen!

## <a name="requirements"></a>Anforderungen

* Visual Studio für Mac Version 7.5 oder höher
* Visual Studio Team Server oder Team Foundation Server 2013 und höher
* Ein Projekt in Visual Studio Team Services oder Team Foundation Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist

## <a name="installation"></a>Installation

Wählen Sie in Visual Studio für Mac den Menüpfad **Visual Studio > Erweiterungen...** aus. Suchen Sie nach „TF-Versionskontrolle“, und installieren Sie die Erweiterung **Team Foundation-Versionskontrolle**. Starten Sie die IDE neu, wenn Sie dazu aufgefordert werden.

## <a name="using-the-add-in"></a>Verwenden des Add-Ins

Sobald die Erweiterung installiert wurde, wählen Sie den Menüpfad **Versionskontrolle > TFS/VSTS > Connect to Team Foundation Version Control...** (Mit Team Foundation-Versionskontrolle verbinden) aus. 

![Hinzufügen eines TFVC-Servers](media/tfvc-add-remove-server.png)


Wählen Sie zum Starten entweder Visual Studio Team Services oder Team Foundation Server aus:

![Verbinden mit einem TFVC-Server](media/tfvc-choose-server-type.png)

Geben Sie Ihre Anmeldeinformationen ein: 

![Anmelden bei einem TFVC-Server](media/tfvc-login.png)

Wählen Sie anschließend die Projekte aus, auf die Sie zugreifen möchten: 

![Auswählen der Projekte](media/tfvc-choose-projects.png)

Schließen Sie zum Fortfahren die Dialogfelder, und verwenden Sie dann den Menüpfad **Versionskontrolle > TFS/VSTS > Quellcodeverwaltungs-Explorer**, um die Quelle zu durchsuchen.

> [!WARNING]
> **Bekanntes Problem**: Bei dieser Vorschauversion muss beim erstmaligen Öffnen des Quellcodeverwaltungs-Explorers ein neuer Arbeitsbereich erstellt werden.

![Quellen-Explorer](media/tfvc-source-explorer.png)

Aus dem Quellcode-Explorer können Sie Ihren Quellcode auf dem Server durchsuchen und folgende Aktionen ausführen:

- Arbeitsbereiche verwalten (erstellen, bearbeiten oder löschen).
- Zwischen Projektstrukturen navigieren.
- Projekte zuordnen.
- Projekte abrufen.
- Dateien sperren und entsperren.
- Dateien umbenennen.
- Dateien löschen.
- Neue Dateien hinzufügen.
- Ausschecken.
- Einchecken.
- Verlaufsänderungen anzeigen.
- Änderungen vergleichen.

## <a name="creating-a-new-workspace"></a>Erstellen eines neuen Arbeitsbereichs

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. 

![Arbeitsbereiche verwalten](media/tfvc-manage-workspaces.png)

Klicken Sie auf **Hinzufügen**, um einen neuen Arbeitsbereich zu erstellen.

![Arbeitsbereich erstellen](media/tfvc-create-workspace.png)

Geben Sie einen Namen für den Arbeitsbereich an, und klicken Sie dann auf **Add Working Folder** (Arbeitsordner hinzufügen), um das Projekt einem lokalen Ordner auf Ihrem Computer zuzuordnen.

Klicken Sie, wenn Sie fertig sind, auf **OK**, und schließen Sie dann das Dialogfeld „Arbeitsbereiche verwalten“. Sie können nun Dateien über den Quellcode-Explorer abrufen und erste Schritte durchführen.