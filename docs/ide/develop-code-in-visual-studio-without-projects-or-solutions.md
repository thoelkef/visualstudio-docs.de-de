---
title: Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code, editing
- code editor, syntax coloring
- code editor [Visual Studio]
- brace matching
- code editor, line numbers
- code editor, brace matching
- line numbers
- syntax coloring
- code editor
- code files
- code
ms.assetid: cb53bb9b-5b76-4759-b9b8-7bf32298bcbb
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 3a8be04b4d2c927dc296753420ff736b993343c9
ms.lasthandoff: 03/07/2017

---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen

In Visual Studio 2017 können Sie Code von Directory-basierten Projekten nahezu jeder Art öffnen, ohne dass eine Projektmappen- oder Projektdatei erforderlich ist. Dies bedeutet: Sie finden z.B. ein Codeprojekt auf Git, klonen es, öffnen es dann direkt in Visual Studio und beginnen mit der Entwicklung, ohne eine Projektmappe oder Projekte erstellen zu müssen.

Sie können nicht nur den Code bearbeiten und in Visual Studio erstellen, sondern auch durch Ihren Code navigieren (z.B. mithilfe des „Navigieren zu“-Befehls). Der Code wird mit Syntaxfarbgebung angezeigt und beinhaltet in vielen Fällen Anweisungsvervollständigung und Debuggen inklusive Haltepunkte in grundlegender Form. Einige Sprachen bieten sogar noch mehr Funktionalität. Weitere Informationen finden Sie unter [Erstellen von portablen, benutzerdefinierten Editor-Einstellungen](create-portable-custom-editor-options.md).

## <a name="open-code-anywhere"></a>Code öffnen – überall
Sie können Code in Visual Studio auf folgende Arten öffnen.
- Wählen Sie in der Visual Studio-Menüleiste **Datei**, **Öffnen**, **Ordner**, und navigieren Sie zum Codespeicherort.
- Wählen Sie im Kontextmenü (Rechtsklick) eines Ordners, der Code enthält, den Befehl **In Visual Studio öffnen** .
- Wählen Sie den Link **Ordner öffnen** auf der Visual Studio-Startseite.
- Öffnen Sie von einem GitHub-Repository geklonten Code.

Das folgende Beispiel zeigt, wie ein GitHub-Repository geklont und dann sein Code in Visual Studio geöffnet wird. Um diese Schritte auszuführen, müssen ein GitHub-Konto und Git für Windows auf Ihrem System installiert sein. Unter [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registrieren für ein neues GitHub-Konto) und [Git for Windows](https://git-for-windows.github.io/) (Git für Windows) finden Sie weitere Informationen.

### <a name="to-open-code-from-a-cloned-github-repo"></a>So öffnen Sie Code aus einem geklonten GitHub-Repository

1. Wechseln Sie zu dem GitHub-Repository, das den Code enthält, den Sie bearbeiten möchten. Zu diesem Zweck benötigen Sie ein GitHub-Konto.
1. Wechseln Sie zu dem Repository, das Sie klonen möchten.
1. Wählen Sie auf der Seite des GitHub-Repositorys die Schaltfläche **Clone or Download** (Klonen oder herunterladen), und wählen Sie dann die Schaltfläche **Copy to Clipboard** (In Zwischenablage kopieren) im Dropdownmenü, um die sichere URL für die GitHub-Website zu kopieren.

  ![Klonenschaltfläche in GitHub](~/ide/media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  Sie haben zwar auch die Möglichkeit, das Projekt auf Ihrem Desktop zu öffnen oder eine ZIP-Datei des Projekts herunterzuladen, doch dieses Beispiel veranschaulicht das Klonen des Repositorys mithilfe einer sicheren URL.

1. Wählen Sie in Visual Studio die Registerkarte **Team Explorer**, um Team Explorer zu öffnen.
1. Wählen Sie in Team Explorer im Abschnitt **Lokale Git-Repositorys** den Befehl **Klonen** aus, und fügen Sie die URL der GitHub-Seite in das Textfeld ein.

  ![Klonen des Projekts](~/ide/media/VSIDE_Code_Clone2.png)

1. Wählen Sie die Schaltfläche **Klonen**, um die Dateien des Projekts in einem lokalen Git-Repository zu klonen. Dies kann je nach Größe des Repositorys einige Minuten dauern.
1. Wählen Sie nach dem Klonen des Repositorys auf Ihrem System in Team Explorer den Befehl **Öffnen** im Kontextmenü (Rechtsklick) des neu geklonten Projekts.

  ![Geklontes Projekt](~/ide/media/VSIDE_Code_Clone3.png)

1. Wählen Sie den Befehl **Ordneransicht anzeigen** aus, um die Dateien im Projektmappen-Explorer anzuzeigen.

  ![Ordneransicht anzeigen](./media/VSIDE_Code_Clone3_show.png)

  Jetzt können Sie Ordner und Dateien im geklonten Projekt durchsuchen und den Code im Code-Editor von Visual Studio anzeigen und durchsuchen, komplett mit Syntaxfarbgebung und anderen Funktionen.

    ![Durchsuchen des geklonten Projektcodes](~/ide/media/VSIDE_Code_Clone4.png)


## <a name="debug-your-code"></a>Debuggen Ihres Codes
Sie können den Code in Visual Studio debuggen. Zum Debuggen bestimmter Sprachen benötigen Sie möglicherweise eine gültige *Startdatei* im Codeprojekt, z.B. ein Skript, eine ausführbare Datei oder eine Projektdatei. In Visual Studio wird dieser angegebene Code zuerst ausgeführt, wenn Sie den Code debuggen.

Auf der Symbolleiste werden in der Dropdownliste neben der Schaltfläche „Start“ sowohl alle Startelemente aufgelistet, die Visual Studio erkennt, als auch die Elemente, die Sie speziell in einem Ordner auswählen.

![Schaltfläche „Ausführen“](~/ide/media/VSIDE_Code_Run_Button.png)

Visual Studio erkennt Projekte automatisch, aber Skripts (z.B. Python und JavaScript) müssen Sie explizit als Startelement auswählen, bevor sie in der Liste angezeigt werden.
Darüber hinaus können einige Startelemente, z.B. MSBuild und CMake, mehrere Buildkonfigurationen verwenden, die in der Dropdownliste der Schaltfläche „Ausführen“ angezeigt werden.

Visual Studio unterstützt derzeit das Debuggen für die folgenden Sprachen:
- Node.js
- Python
- MSBuild-basierte Projekte (C#, VB, C++)
- Jede ausführbare Datei mit PDB-Dateien (Python-Debugger).

### <a name="to-debug-nodejs-and-python"></a>So debuggen Sie Node.js und Python:
1. Installieren Sie Node.js- oder Python-Tools oder Visual Studio 2017 und die Node.js-Laufzeit.
1. Wählen Sie im Kontextmenü einer JavaScript-Datei im Projektmappen-Explorer den Befehl **Als Startelement festlegen**.
1. Drücken Sie die F5-Taste, um das Debuggen zu starten.

### <a name="to-debug-msbuild-projects"></a>So debuggen Sie MSBuild-Projekte
1. Wählen Sie im Visual Studio-Menü **Debuggen**. Wählen Sie im Dropdownmenü das Projekt, oder wählen Sie das Projekt bzw. die Datei, das/die als Startelement im Projektmappen-Explorer angezeigt werden soll.
1. Drücken Sie die F5-Taste, um das Debuggen zu starten.

### <a name="to-debug-executable-files"></a>So debuggen Sie ausführbare Dateien
1. Wählen Sie im Visual Studio-Menü **Debuggen**. Wählen Sie im Dropdownmenü das Projekt, oder wählen Sie das Projekt bzw. die Datei, das/die als Startelement im Projektmappen-Explorer angezeigt werden soll.
1. Drücken Sie die F5-Taste, um das Debuggen zu starten.


## <a name="enable-custom-build-tools"></a>Aktivieren benutzerdefinierter Buildtools
Visual Studio weiß, wie viele verschiedene Sprachen ausgeführt werden, aber nicht, wie alles ausgeführt wird. Wenn Visual Studio weiß, wie Ihre Sprache ausgeführt wird, können Sie den Code sofort ausführen. Wenn Sie versuchen, den Code auszuführen, aber Visual Studio nicht weiß, wie er ausgeführt wird, werden Sie in einer Informationsleiste aufgefordert, eine Datei in Ihrer Codebasis als Startelement festzulegen .

Wenn die Codebasis benutzerdefinierte Buildtools verwendet, die Visual Studio jedoch nicht erkennt, können Sie den Code wahrscheinlich nicht in Visual Studio ausführen und debuggen (z.B. durch Auswählen der F5-Taste), bis Sie einen gültigen ausführbaren Dateityp (z.B. einen Compiler) sowie alle benutzerdefinierten Parameter und Argumente angeben, die die Sprache benötigt. Um dies zu ermöglichen, bietet Visual Studio *Buildtasks*. Sie können eine Buildaufgabe erstellen, um alle Elemente anzugeben, die eine Sprache benötigt, um ihren Code zu erstellen und auszuführen.

Sie können auch beliebige Buildaufgaben erstellen, die nahezu alles tun können, was Sie möchten. Beispielsweise können Sie eine Aufgabe erstellen, um den Inhalt eines Ordners aufzulisten oder eine Datei umzubenennen. Sie können auch gezieltere benutzerdefinierte Buildaufgaben erstellen, die mithilfe bestimmter Argumente Aktionen wie das Kompilieren und Erstellen Ihres Projekts ausführen. Die folgenden Schritte zeigen das Erstellen beider Arten von Buildaufgaben.

#### <a name="to-create-an-arbitrary-build-task"></a>So erstellen Sie eine beliebige Buildaufgabe

1. Wählen Sie die Datei oder den Ordner des Projekts im Projektmappen-Explorer aus, wo die Aufgabe gespeichert werden soll, und klicken Sie auf das Kontextmenü (Rechtsklick) der Datei oder des Ordners, und wählen Sie **Tasks konfigurieren**.

  ![Tasks konfigurieren](~/ide/media/VSIDE_Code_Config_Task.png)

  Bei Auswahl von **Tasks konfigurieren** wird die Datei „tasks.vs.json“ geöffnet. Wenn diese Datei nicht vorhanden ist, wird sie erstellt. Diese Datei enthält die Buildaufgaben für die ausgewählte Datei oder den Ordner.

  ![Datei „tasks.vs.json“](~/ide/media/VSIDE_Code_Tasks_JSON.png)

1. Fügen Sie „tasks.vs.json“ die folgende Buildaufgabe hinzu. In diesem Beispiel fügen wir eine einfache Aufgabe „List outputs“ hinzu, die Dateien und Unterordner des ausgewählten Ordners im Fenster „Ausgabe“ auflistet. (Die neue Aufgabe sollte innerhalb des vorhandenen Arrays „tasks“ hinzugefügt werden.)

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  Die vollständige Buildaufgabe sollte wie folgt aussehen.

  ![Beliebige Buildaufgabe](~/ide/media/VSIDE_Code_Tasks_ArbTask.png)

1. Speichern Sie das Projekt.
1. Öffnen Sie das Kontextmenü für den ausgewählten Ordner. Sie sollten nun die neue beliebige Buildaufgabe sehen, die am unteren Rand im Kontextmenü angezeigt werden sollte.

  ![Beliebige Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_ArbTask2.png)

1. Wählen Sie den neuen Befehl **List outputs** aus, um die Aufgabe auszuführen.


### <a name="to-create-a-custom-build-task"></a>So erstellen Sie eine benutzerdefinierte Buildaufgabe
In diesem Verfahren fügen wir zwei benutzerdefinierte Buildaufgaben hinzu, die nMake verwenden, um Ihren Code zu erstellen und zu bereinigen.

1. Wählen Sie eine Datei des Projekts im Projektmappen-Explorer aus, die Sie später als Startelement festlegen möchten. Wählen Sie im Kontextmenü (Rechtsklick) der Datei **Tasks konfigurieren**.

  ![Benutzerdefinierte Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_CustTask1.png)

1. Fügen Sie „tasks.vs.json“ die folgenden Buildaufgaben hinzu. In diesem Beispiel werden zwei Aufgaben hinzugefügt: eine namens „makefile-build“, die den nMake-Befehl verwendet, um das Projekt zu erstellen, die andere mit der Bezeichnung „makefile-clean“ ruft den nMake-Befehl mit dem Argument „clean“ auf. Diese Aufgaben sollten innerhalb des vorhandenen Arrays „tasks“ hinzugefügt werden. (Beachten Sie, dass dies nur Beispielbuildaufgaben sind. Damit sie tatsächlich funktionieren, muss die Arbeitsauslastung, die [nNake](https://docs.microsoft.com/en-us/cpp/build/nmake-reference) enthält, auf Ihrem System installiert sein.)

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  Die vollständige benutzerdefinierte Buildaufgabe sollte wie folgt aussehen.

  ![Benutzerdefinierte Buildaufgabe](~/ide/media/VSIDE_Code_Tasks_CustTask2.png)

1. Speichern Sie das Projekt.
1. Öffnen Sie das Kontextmenü für die ausgewählte Datei. Die neuen benutzerdefinierten Buildaufgaben sollten in der Mitte des Kontextmenüs angezeigt werden.

  ![Benutzerdefinierte Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > Die Befehle werden aufgrund ihrer `contextType`-Einstellungen unter dem Befehl **Tasks konfigurieren** angezeigt; „build“und „clean“ sind Buildbefehle, sodass sie im Buildabschnitt in der Mitte des Kontextmenüs angezeigt werden.

  Da Sie nun benutzerdefinierte Buildbefehle mit der Datei verknüpft haben, können Sie die Datei als Startelement festlegen.

1. Wählen Sie im Kontextmenü der Datei **Als Startelement festlegen**.

  ![Benutzerdefinierte Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_CustTask4.png)

1. Wählen Sie auf der Symbolleiste den Dropdownpfeil neben der Schaltfläche „Start“. Das Startelement wird jetzt als Option angezeigt.

  ![Benutzerdefinierte Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_CustTask5.png)

Sie können jetzt die Schaltfläche „Start“ oder die F5-Taste zum Ausführen Ihrer Codebasis auswählen. Sie können Ihre Codebasis in Visual Studio bearbeiten und debuggen, auch wenn Visual Studio die Buildtools der Codebasis nicht erkennt. Die Ausgabe der Buildaufgabe wird im Fenster **Ausgabe** angezeigt, und die Buildfehler werden in der **Fehlerliste** angezeigt. Die Buildaufgabendatei „tasks.vs.json“ koppelt die innere Entwicklungschleife von Visual Studio mit den benutzerdefinierten Buildtools, die Ihre Codebasis verwendet.

Benutzerdefinierte Buildaufgaben können einzelnen Dateien oder allen Dateien eines bestimmten Typs hinzugefügt werden. NuGet-Paketdateien können z.B. mit einer „Restore Packages“-Aufgabe konfiguriert werden, oder alle Quelldateien können so konfiguriert werden, dass sie eine statische Analyseaufgabe haben, z.B. einen Linter für alle JS-Dateien.

Visual Studio unterstützt die VSCode-`$variable`-Ersetzung im Stammverzeichnis von „tasks.vs.json“, zusätzlich zu den Umgebungsvariablen (z.B. `$env.var`) oder Schlüsseln.

## <a name="specify-build-output"></a>Angeben der Buildausgabe
Wenn das Projekt kompiliert werden muss, können Sie der tasks.vs.json-Datei ein zusätzliches Tag namens `output` hinzufügen. Im Folgenden ein Beispiel.

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

Wenn Sie den Ausgabespeicherort angeben, weiß Visual Studio, wo die Buildausgabe des Projekts zu finden ist.


## <a name="tasksvsjson-file-location"></a>Speicherort der Datei „tasks.vs.json“

Standardmäßig befindet sich die Datei „tasks.vs.json“ in einem ausgeblendeten Ordner namens `.vs`. Wählen Sie zum Anzeigen ausgeblendeter Dateien in Visual Studio die Schaltfläche **Alle Dateien anzeigen** auf der Symbolleiste des Projektmappen-Explorers.

![Beliebige Buildaufgabe, Befehl](~/ide/media/VSIDE_Code_Tasks_FileLocation.png)

Die Datei „tasks.vs.json“ wird ausgeblendet, da die meisten Benutzer sie in der Regel nicht in die Quellcodeverwaltung einchecken möchten. Wenn Sie jedoch die Möglichkeit haben möchten, sie in die Quellcodeverwaltung einzuchecken, ziehen Sie die Datei in das Stammverzeichnis Ihres Projekts, wo sie sichtbar ist.

Andere JSON-Dateien sind möglicherweise im VS-Ordner vorhanden, aber Sie sollten nur die Datei „tasks.vs.json“ und „launch.vs.json“ (sofern vorhanden) verschieben. Die Datei „launch.vs.json“ konfiguriert den Visual Studio-Debugger, während die Datei „tasks.vs.json“ den Build in Visual Studio konfiguriert.

