---
title: Verwenden der Visual Studio für Mac-Tools für Unity
description: In diesem Leitfaden wird erklärt, wie Sie die Erweiterung Visual Studio für Mac-Tools für Unity verwenden.
author: dantogno
ms.author: v-davian
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: ab605b3a8505ac189bc0f628b717c6863f9fd902
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Verwenden der Visual Studio für Mac-Tools für Unity

In diesem Abschnitt erfahren Sie, wie Sie die Integrations- und Produktivitätsfunktionen der Visual Studio für Mac-Tools für Unity und den Visual Studio für Mac-Debugger für die Unity-Entwicklung einsetzen.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Öffnen von Unity-Skripts in Visual Studio für Mac

Nachdem Sie Visual Studio für Mac als [externen Skript-Editor für Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac) festgelegt haben, wird durch das Öffnen eines Skripts über den Unity-Editor Visual Studio für Mac automatisch gestartet oder dahin gewechselt, während das ausgewählte Skript geöffnet ist.

Alternativ können Sie Visual Studio für Mac öffnen, während kein Skript im Quellcode-Editor geöffnet ist. Wählen Sie dazu im Menü **Assets** (Bestand) in Unity **Open C# Project** (C#-Projekt öffnen) aus.

![Öffnen eines C#-Projekts](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Zugriff auf die Unity-Dokumentation

Die Visual Studio für Mac-Tools für Unity enthalten eine Verknüpfung für den Zugriff auf die Unity-API-Dokumentation. Um auf Unity API-Dokumentation von Visual Studio für Mac zuzugreifen, platzieren Sie den Cursor auf der Unity API, über die Sie mehr erfahren möchten, und drücken Sie **⌘ (cmd)+‘**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense für Unity-Nachrichten
Die Unity-Engine sendet Nachrichten an MonoBehaviour-Skripts, die es Entwicklern ermöglichen, Code zu schreiben, der auf Meldungen wie „OnMouseDown“, „OnTriggerEnter“ usw. reagiert. Da es keine virtuellen Methoden in der Basisklasse von MonoBehaviour gibt, fehlen einigen IDEs wie MonoDevelop die Funktion zur Codevervollständigung für Unity-Nachrichten.

Die Visual Studio für Mac-Tools für Unity erweitern Ihre IntelliSense-Funktionalität aber auf Unity-Nachrichten. Dies erleichtert das Implementieren von Unity-Nachrichten in MonoBehaviour-Skripts und das Erlernen des Umgangs mit der Unity-API. So verwenden Sie IntelliSense für Unity-Nachrichten:

1.  Platzieren Sie den Cursor in einer neuen Zeile innerhalb des Texts einer Klasse, die von MonoBehaviour abgeleitet wird.

2.  Geben Sie den Namens einer Unity-Nachricht ein, z.B. `OnTriggerEnter`.

3.  Sobald Sie die Buchstaben **ont** eingegeben haben, wird eine Liste von IntelliSense-Vorschlägen angezeigt.

  ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4.  Die Auswahl in der Liste kann auf drei verschiedene Arten geändert werden:

    * Mit den Pfeiltasten **Nach oben** und **Nach unten**

    * Indem Sie mit der Maus auf das gewünschte Element klicken

    * Indem Sie den Namen des gewünschten Elements weiter eingeben

5.  IntelliSense kann die ausgewählte Unity-Nachricht einfügen, einschließlich aller erforderlichen Parameter:

    * Durch Drücken der **TAB-TASTE**

    * Durch Drücken der **EINGABETASTE**

    * Durch Doppelklicken auf das ausgewählte Element

  ![Einfügen von Unity-Nachrichten über IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Hinzufügen neuer Unity-Dateien und -Ordner

Sie können einem Unity-Projekt im Unity-Editor zwar immer neue Dateien hinzufügen, in Visual Studio für Mac hingegen lassen sich problemlos neue Unity-Skripts, -Shader und -Ordner innerhalb von Visual Studio erstellen.

### <a name="add-a-new-c-monobehaviour-script"></a>Hinzufügen eines neuen C#-MonoBehaviour-Skripts

Um ein neues C#-MonoBehaviour-Skript hinzuzufügen, **klicken Sie mit der rechten Maustaste auf den Ordner „Assets“** oder eines der Unterverzeichnisse in der Projektmappe, und wählen Sie **Hinzufügen > New MonoBehaviour** (Neues MonoBehaviour-Skript) aus.

![Neues MonoBehaviour-Skript hinzufügen](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Hinzufügen eines neuen Unity-Shaders

Um einen neuen Unity-Shader hinzuzufügen, **klicken Sie mit der rechten Maustaste auf den Ordner „Assets“** oder ein Unterverzeichnis im Verzeichnis der Projektmappe, und wählen Sie **Hinzufügen > New Shader** (Neuer Shader) aus.

### <a name="add-a-new-folder"></a>Hinzufügen eines neuen Ordners

Um einen neuen Ordner hinzuzufügen, **klicken Sie mit der rechten Maustaste auf den Ordner „Assets“** oder ein Unterverzeichnis im Verzeichnis der Projektmappe, und wählen Sie **Hinzufügen > New Folder** (Neuer Ordner) aus.

Diese Hinzufügungen werden im Projektfenster des Unity-Editors wiedergegeben.

### <a name="to-rename-a-file-or-folder"></a>So benennen Sie eine Datei oder einen Ordner um
**Klicken Sie mit der rechten Maustaste** auf das umzubenennende Element in der Projektmappe, und wählen Sie **Rename...** (Umbenennen...) aus.

> [!NOTE]
> Wenn Sie ein neues Unity-Projekt ohne Skripts haben, und der Ordner „Assets“ nicht in der Projektmappe in Visual Studio für Mac angezeigt wird, fügen Sie ein anfängliches C#-Skript über den Unity-Editor hinzu.

## <a name="unity-debugging"></a>Debuggen von Unity

Unity-Projekte können mit Visual Studio für Mac gedebuggt werden.

### <a name="start-debugging"></a>Debugging starten

Starten des Debuggens:

1.  Verbinden Sie Visual Studio mit Unity, indem Sie auf die Schaltfläche **Play** (Wiedergeben) klicken, oder drücken Sie **⌘ (cmd)+EINGABETASTE** oder **F5** ein.

  ![In Visual Studio auf „Wiedergeben“ klicken](media/using-vsmac-tools-unity-image5.png)

2.  Wechseln Sie zu Unity, und klicken Sie auf **Play**, um das Spiel im Editor auszuführen.

  ![In Unity auf „Wiedergeben“ klicken](media/using-vsmac-tools-unity-image6.png)

3.  Wenn das Spiel in Unity-Editor ausgeführt wird und gleichzeitig ein Verbindung mit Visual Studio besteht, pausieren alle vorgefundenen Breakpoints die Ausführung des Spiels und bringen die Codezeile hervor, in der das Spiel den Breakpoint in Visual Studio für Mac erreicht hat.

### <a name="stop-debugging"></a>Beenden des Debuggens

So beenden Sie das Debuggen:

1.  Klicken Sie in Visual Studio für Mac auf **Stop** (Beenden), oder drücken Sie **UMSCHALTTASTE+CMD+EINGABETASTE**.

  ![In Visual Studio auf „Beenden“ klicken](media/using-vsmac-tools-unity-image7.png)

Weitere Informationen zum Debuggen in Visual Studio für Mac finden Sie unter [Verwenden des Debuggers](https://docs.microsoft.com/visualstudio/mac/debugging).
