---
title: Tutorial zur Hallo Welt-Erweiterung | Microsoft-Dokumentation
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404141"
---
# <a name="create-your-first-extension-hello-world"></a>Erstellen Sie Ihre erste Erweiterung: Hallo Welt

Dieses Hallo Welt Beispiel führt Sie durch die Erstellung Ihrer ersten Erweiterung für Visual Studio. In diesem Tutorial wird gezeigt, wie Sie Visual Studio einen neuen Befehl hinzufügen.

In diesem Prozess lernen Sie Folgendes:

* **[Erstellen eines Erweiterbarkeits Projekts](#create-an-extensibility-project)**
* **[Hinzufügen eines benutzerdefinierten Befehls](#add-a-custom-command)**
* **[Ändern des Quellcodes](#modify-the-source-code)**
* **[Ausführen](#run-it)**

In diesem Beispiel verwenden Sie Visual C# zum Hinzufügen einer benutzerdefinierten Menü Schaltfläche mit dem Namen "Say Hallo Welt!". Das sieht wie folgt aus:

![Hallo Welt-Befehl](media/hello-world-say-hello-world.png)

> [!NOTE]
> Dieser Artikel bezieht sich auf Visual Studio unter Windows. Visual Studio für Mac finden Sie unter Exemplarische Vorgehensweise für die [Erweiterbarkeit in Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie beginnen, stellen Sie sicher, dass Sie die Arbeitsauslastung für die **Visual Studio-Erweiterungs Entwicklung** installiert haben, die die erforderliche VSIX-Vorlage und den Beispielcode enthält.

> [!NOTE]
> Sie können eine beliebige Edition von Visual Studio (Community, Professional oder Enterprise) verwenden, um ein Visual Studio-Erweiterbarkeits Projekt zu erstellen.

## <a name="create-an-extensibility-project"></a>Erstellen eines Erweiterbarkeits Projekts

::: moniker range="vs-2017"

Schritt 1. Wählen Sie im Menü **Datei** den Befehl **Neu** > **Projekt** aus.

Schritt 2. Geben Sie im Suchfeld in der oberen rechten Ecke "VSIX" ein, und wählen Sie C# das Visual **VSIX-Projekt**aus. Geben Sie "HelloWorld" für den **Namen** unten im Dialogfeld ein, und klicken Sie auf **OK**.

![Neues Projekt](media/hello-world-new-project.png)

Nun sollten Sie die Seite "Getting Started" und einige Beispiel Ressourcen sehen.

Wenn Sie dieses Lernprogramm verlassen und darauf zurückkehren müssen, finden Sie das neue Projekt "HelloWorld" auf der **Start Seite** im **letzten** Abschnitt.

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1. Wählen Sie im Menü **Datei** den Befehl **Neu** > **Projekt** aus. Suchen Sie nach "VSIX", und wählen C# Sie das Visual **VSIX-Projekt** und dann **weiter**aus.

Schritt 2. Geben Sie "HelloWorld" als **Projektnamen** ein, und klicken Sie auf **Erstellen**.

![Neues Projekt](media/hello-world-new-project-2019.png)

Das Projekt HelloWorld sollte nun in **Projektmappen-Explorer**angezeigt werden.

::: moniker-end

## <a name="add-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls

Schritt 1. Wenn Sie die *vsixmanifest* -Manifest-Datei auswählen, können Sie sehen, welche Optionen änderbar sind, z. b. Beschreibung, Autor und Version.

Schritt 2. Klicken Sie mit der rechten Maustaste auf das Projekt (nicht die Projekt Mappe). Wählen Sie im Kontextmenü **Hinzufügen**und dann **Neues Element**aus.

Schritt 3 Wählen Sie den Abschnitt **Erweiterbarkeit** aus, und klicken Sie dann auf **Befehl**.

Schritt 4. Geben Sie im Feld **Name** unten einen Dateinamen ein, z. b. *Command.cs*.

![benutzerdefinierter Befehl](media/hello-world-vsix-command.png)

Die neue Befehlsdatei ist in **Projektmappen-Explorer**sichtbar. Unter dem Knoten **Ressourcen** finden Sie weitere Dateien im Zusammenhang mit dem Befehl. Wenn Sie z. b. das Image ändern möchten, befindet sich die PNG-Datei hier.

## <a name="modify-the-source-code"></a>Ändern des Quellcodes

An diesem Punkt werden der Befehl und der Schaltflächen Text automatisch generiert und sind nicht sehr interessant. Sie können die vsct-Datei und die CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* In der vsct-Datei können Sie die Befehle umbenennen und definieren, wohin Sie im Visual Studio-Befehlssystem wechseln. Beim Durchsuchen der vsct-Datei werden Kommentare angezeigt, in denen erläutert wird, was die einzelnen Abschnitte der vsct-Code-Steuerelemente sind.

* In der CS-Datei können Sie Aktionen definieren, z. b. den Click-Handler.

::: moniker range="vs-2017"

Schritt 1. Suchen Sie in **Projektmappen-Explorer**nach der vsct-Datei für Ihren neuen Befehl. In diesem Fall wird Sie als *commandpackage. vsct*bezeichnet.

![vsct des Befehls Pakets](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1. Suchen Sie in **Projektmappen-Explorer**nach der vsct-Datei für Ihre Erweiterung im Vergleich zum Paket. In diesem Fall wird Sie als " *helloworldpackage. vsct*" bezeichnet.

::: moniker-end

Schritt 2. Ändern Sie den `ButtonText`-Parameter in `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Schritt 3 Wechseln Sie zurück zu **Projektmappen-Explorer** , und suchen Sie die Datei *Command.cs* . Ändern Sie in der `Execute`-Methode die Zeichenfolge `message` von `string.Format(..)` in `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Stellen Sie sicher, dass Sie die Änderungen an jeder Datei speichern.

## <a name="run-it"></a>Führen Sie das Skript aus.

Sie können nun den Quellcode in der experimentellen Instanz von Visual Studio ausführen.

Schritt 1. Drücken Sie **F5** , um den Befehl **Debuggen starten** auszuführen. Dieser Befehl erstellt das Projekt und startet den Debugger, wobei eine neue Instanz von Visual Studio gestartet wird, die als **experimentelle Instanz**bezeichnet wird.

::: moniker range="vs-2017"

In der Titelleiste von Visual Studio wird die **experimentelle Instanz** angezeigt.

![Titelleiste der experimentellen Instanz](media/hello-world-exp-instance.png)

::: moniker-end

Schritt 2. Klicken Sie **im Menü Extras** der **experimentellen Instanz**auf **Hallo Welt!** .

![Endgültiges Ergebnis](media/hello-world-final-result.png)

Die Ausgabe des neuen benutzerdefinierten Befehls sollte angezeigt werden, in diesem Fall das Dialogfeld in der Mitte des Bildschirms, in dem Sie die **Hallo Welt erhalten!** Vorgang nicht gefunden werden konnte.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun mit den Grundlagen der Visual Studio-Erweiterbarkeit vertraut sind, finden Sie hier weitere Informationen:

* [Beginnen Sie mit der Entwicklung von Visual Studio-Erweiterungen](starting-to-develop-visual-studio-extensions.md) : Beispiele, Tutorials. und Veröffentlichen der Erweiterung
* [Neues in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) : neue Erweiterbarkeits Funktionen in Visual Studio 2017
* [Neues in Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) : neue Erweiterbarkeits Funktionen in Visual Studio 2019
* [Im Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) : Erlernen Sie die Details der Visual Studio-Erweiterbarkeit.
