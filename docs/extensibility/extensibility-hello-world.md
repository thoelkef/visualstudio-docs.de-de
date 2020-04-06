---
title: Hallo Welt Erweiterung Tutorial | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711665"
---
# <a name="create-your-first-extension-hello-world"></a>Erstellen Sie Ihre erste Erweiterung: Hello World

In diesem Hello World-Beispiel werden Sie durch das Erstellen Ihrer ersten Erweiterung für Visual Studio geführt. In diesem Tutorial erfahren Sie, wie Sie Visual Studio einen neuen Befehl hinzufügen.

Dabei erfahren Sie:

* **[Erstellen eines Erweiterbarkeitsprojekts](#create-an-extensibility-project)**
* **[Hinzufügen eines benutzerdefinierten Befehls](#add-a-custom-command)**
* **[Ändern des Quellcodes](#modify-the-source-code)**
* **[Führen Sie das Skript aus.](#run-it)**

In diesem Beispiel fügen Sie mit Visual C- eine benutzerdefinierte Menüschaltfläche mit dem Namen "Say Hello World!" hinzu. das sieht wie folgt aus:

![Hello World-Befehl](media/hello-world-say-hello-world.png)

> [!NOTE]
> Dieser Artikel gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Exemplarische Vorgehensweise für Erweiterbarkeit in Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** installiert haben, die die gewünschte VSIX-Vorlage und Beispielcode enthält.

> [!NOTE]
> Sie können jede Edition von Visual Studio (Community, Professional oder Enterprise) verwenden, um ein Visual Studio-Erweiterbarkeitsprojekt zu erstellen.

## <a name="create-an-extensibility-project"></a>Erstellen eines Erweiterbarkeitsprojekts

::: moniker range="vs-2017"

Schritt 1: Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**.

Schritt 2: Geben Sie im Suchfeld oben rechts "vsix" ein, und wählen Sie das Visual **C-VSIX-Projekt**aus. Geben Sie "HelloWorld" für den **Namen** am unteren Rand des Dialogfelds ein und wählen Sie **OK**.

![Neues Projekt](media/hello-world-new-project.png)

Sie sollten nun die Seite Erste Schritte und einige Beispielressourcen sehen.

Wenn Sie dieses Tutorial verlassen und darauf zurückkommen müssen, können Sie Ihr neues HelloWorld-Projekt auf der **Startseite** im Abschnitt **"Zuletzt"** finden.

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1: Klicken Sie im Menü **Datei** auf **Neu** > **Projekt**. Suchen Sie nach "vsix", und wählen Sie das Visual-VSIX-Projekt und dann **Weiter**aus. **VSIX Project**

Schritt 2: Geben Sie "HelloWorld" für den **Projektnamen ein** und wählen Sie **Erstellen**aus.

![Neues Projekt](media/hello-world-new-project-2019.png)

Das HelloWorld-Projekt sollte nun im **Projektmappen-Explorer**angezeigt werden.

::: moniker-end

## <a name="add-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls

Schritt 1: Wenn Sie die *.vsixmanifest-Manifestdatei* auswählen, können Sie sehen, welche Optionen geändert werden können, z. B. Beschreibung, Autor und Version.

Schritt 2: Klicken Sie mit der rechten Maustaste auf das Projekt (nicht auf die Projektmappe). Wählen Sie im Kontextmenü **Hinzufügen**aus, und dann **neue Elemente**.

Schritt 3: Wählen Sie den Abschnitt **Erweiterbarkeit** aus, und wählen Sie dann **Befehl**aus.

Schritt 4. Geben Sie im Feld **Name** unten einen Dateinamen ein, z. B. *Command.cs*.

![Benutzerdefinierter Befehl](media/hello-world-vsix-command.png)

Ihre neue Befehlsdatei ist im **Projektmappen-Explorer**sichtbar. Unter dem Knoten **Ressourcen** finden Sie weitere Dateien, die sich auf Ihren Befehl beziehen. Wenn Sie beispielsweise das Bild ändern möchten, befindet sich die PNG-Datei hier.

## <a name="modify-the-source-code"></a>Ändern des Quellcodes

An diesem Punkt werden der Befehl und der Button-Text automatisch generiert und nicht sehr interessant. Sie können die VSCT-Datei und die CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* In der VSCT-Datei können Sie Ihre Befehle umbenennen und definieren, wo sie im Visual Studio-Befehlssystem angezeigt werden. Wenn Sie die VSCT-Datei untersuchen, werden Sie Kommentare bemerken, die erklären, was jeder Abschnitt des VSCT-Codes steuert.

* In der CS-Datei können Sie Aktionen definieren, z. B. den Klickhandler.

::: moniker range="vs-2017"

Schritt 1: Suchen Sie im **Projektmappen-Explorer**die VSCT-Datei für Ihren neuen Befehl. In diesem Fall wird es *CommandPackage.vsct*heißen.

![Befehlspaket vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1: Suchen Sie im **Projektmappen-Explorer**nach der VSCT-Datei für Ihr Erweiterungspaket VS. In diesem Fall wird es *HelloWorldPackage.vsct*heißen.

::: moniker-end

Schritt 2: Ändern `ButtonText` Sie `Say Hello World!`den Parameter in .

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

Schritt 3: Kehren Sie zum **Projektmappen-Explorer** zurück, und suchen Sie die *Command.cs-Datei.* Ändern `Execute` Sie in der `message` `string.Format(..)` Methode `Hello World!`die Zeichenfolge von in .

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

Sie können nun den Quellcode in der Visual Studio Experimental-Instanz ausführen.

Schritt 1: Drücken Sie **F5,** um den Befehl **Debugging starten** auszuführen. Dieser Befehl erstellt Ihr Projekt und startet den Debugger, indem eine neue Instanz von Visual Studio namens **Experimental Instance**gestartet wird.

::: moniker range="vs-2017"

Die Wörter **Experimentelle Instanz** werden in der Visual Studio-Titelleiste angezeigt.

![experimentelle Instanztitelleiste](media/hello-world-exp-instance.png)

::: moniker-end

Schritt 2: Klicken Sie im Menü **Extras** der **Experimental Instance**auf **"Hallo Welt sagen!"**.

![Endergebnis](media/hello-world-final-result.png)

Sie sollten die Ausgabe von Ihrem neuen benutzerdefinierten Befehl sehen, in diesem Fall das Dialogfeld in der Mitte des Bildschirms, der Ihnen die **Hello World gibt!** Meldung.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun die Grundlagen der Arbeit mit Visual Studio Extensibility kennen, erfahren Sie hier mehr:

* [Beginnen Sie mit der Entwicklung von Visual Studio-Erweiterungen](starting-to-develop-visual-studio-extensions.md) - Beispiele, Tutorials. und veröffentlichen Sie Ihre Erweiterung
* [Neuerungen im Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) - Neue Erweiterbarkeitsfeatures in Visual Studio 2017
* [Neuerungen im Visual Studio 2019 SDK](whats-new-visual-studio-2019-sdk.md) - Neue Erweiterbarkeitsfeatures in Visual Studio 2019
* [Im Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) – Erfahren Sie mehr über die Visual Studio-Erweiterbarkeit
