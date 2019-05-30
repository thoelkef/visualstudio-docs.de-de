---
title: Hello World-Erweiterung-Lernprogramm | Microsoft-Dokumentation
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c3bbafcf138c60b65940bcee73c74f56cf6e2fd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342865"
---
# <a name="create-your-first-extension-hello-world"></a>Erstellen Sie Ihrer erste Erweiterung: Hello World

Dieses Hello World-Beispiel führt Sie durch die Erstellung Ihrer ersten Erweiterungs für Visual Studio. In diesem Tutorial erfahren Sie, wie Visual Studio einen neuen Befehl hinzugefügt werden.

In den Prozess, erfahren Sie, wie Sie:

* **[Erstellen Sie ein Erweiterungsprojekt](#create-an-extensibility-project)**
* **[Fügen Sie einen benutzerdefinierten Befehl hinzu](#add-a-custom-command)**
* **[Der Quellcode geändert](#modify-the-source-code)**
* **[Führen Sie es](#run-it)**

In diesem Beispiel verwenden Visual C#-Sie beim Hinzufügen eine benutzerdefinierten Menüschaltfläche "Z. B. Hello World!" Das sieht folgendermaßen aus:

![Hello World-Befehl](media/hello-world-say-hello-world.png)

> [!NOTE]
> Dieser Artikel gilt für Visual Studio unter Windows. Visual Studio für Mac finden Sie unter [Erweiterbarkeit Exemplarische Vorgehensweise in Visual Studio für Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Vorraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie installiert die **Visual Studio-extensionentwicklung** arbeitsauslastung aus, die die VSIX-Vorlage enthält, Sie benötigen sowie Beispielcode.

> [!NOTE]
> Sie können eine beliebige Edition von Visual Studio (Community, Professional oder Enterprise) zum Erstellen eines Visual Studio-Erweiterbarkeit-Projekts verwenden.

## <a name="create-an-extensibility-project"></a>Erstellen Sie ein Erweiterungsprojekt

::: moniker range="vs-2017"

Schritt 1. Wählen Sie im Menü **Datei** den Befehl **Neu** > **Projekt** aus.

Schritt 2 Klicken Sie in das Suchfeld in der oberen rechten Ecke, geben Sie "Vsix", und wählen Sie die Visualisierung C# **VSIX-Projekt**. Geben Sie "HelloWorld" für die **Namen** am unteren Rand Dialogfeld, und klicken **OK**.

![Neues Projekt](media/hello-world-new-project.png)

Die Seite Erste Schritte und einige Beispielressourcen sollte jetzt angezeigt werden.

Wenn Sie lassen dieses Tutorial, und warten müssen, finden Sie das neue HelloWorld-Projekt auf die **Startseite** in die **zuletzt** Abschnitt.

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1. Wählen Sie im Menü **Datei** den Befehl **Neu** > **Projekt** aus. Suchen Sie nach "Vsix", und wählen Sie die Visualisierung C# **VSIX-Projekt** und dann **Weiter**.

Schritt 2 Geben Sie "HelloWorld" für die **Projektname** , und wählen Sie **erstellen**.

![Neues Projekt](media/hello-world-new-project-2019.png)

Daraufhin sollte das HelloWorld-Projekt in **Projektmappen-Explorer**.

::: moniker-end

## <a name="add-a-custom-command"></a>Fügen Sie einen benutzerdefinierten Befehl hinzu

Schritt 1. Bei Auswahl der *vsixmanifest* Manifestdatei, Sie können sehen, welche Optionen geändert werden, z. B. Beschreibung, Autor und Version sind.

Schritt 2 Mit der rechten Maustaste in des Projekts (nicht auf die Projektmappe). Wählen Sie im Kontextmenü des **hinzufügen**, und klicken Sie dann **neues Element**.

Schritt 3 Wählen Sie die **Erweiterbarkeit** aus, und wählen Sie dann **benutzerdefinierten Befehls**.

Schritt 4. In der **Namen** Feld am unteren Rand, geben Sie einen Dateinamen z. B. *Command.cs*.

![benutzerdefinierter Befehl](media/hello-world-custom-command.png)

Die neue Befehlsdatei werden in **Projektmappen-Explorer**. Unter den **Ressourcen** Knoten finden Sie weitere Dateien, die im Zusammenhang mit dem Befehl. Wenn Sie das Bild ändern möchten, ist beispielsweise die PNG-Datei hier.

## <a name="modify-the-source-code"></a>Der Quellcode geändert

An diesem Punkt die Befehls- und der Text der Schaltfläche automatisch generiert werden und nicht sehr interessant. Sie können die VSCT-Datei, und die CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* VSCT-Datei ist, in dem Sie können Ihre Befehle umbenennen sowie definieren, in dem sie das System der Visual Studio-Befehl wechseln Sie in. Wenn Sie die VSCT-Datei untersuchen, bemerken Sie Kommentare, die erläutern, die für jeden Abschnitt der VSCT-Code-Steuerelemente.

* Die CS-Datei ist, in denen Sie Aktionen wie das Click-Ereignishandler definieren können.

::: moniker range="vs-2017"

Schritt 1. In **Projektmappen-Explorer**, suchen Sie die VSCT-Datei für den neuen Befehl. In diesem Fall wird Sie aufgerufen *CommandPackage.vsct*.

![Befehl Paket vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Schritt 1. In **Projektmappen-Explorer**, VSCT-Datei für Ihre Visual Studio-Erweiterungspaket zu finden. In diesem Fall wird Sie aufgerufen *HelloWorldPackage.vsct*.

::: moniker-end

Schritt 2 Ändern der `ButtonText` Parameter `Say Hello World!`.

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

Schritt 3 Wechseln Sie zurück zur **Projektmappen-Explorer** und suchen Sie die *Command.cs* Datei. In der `Execute` -Methode, ändern Sie die Zeichenfolge `message` aus `string.Format(..)` zu `Hello World!`.

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

Stellen Sie sicher, dass die Änderungen in jeder Datei zu speichern.

## <a name="run-it"></a>Führen Sie es

Sie können nun den Quellcode in der experimentellen Visual Studio-Instanz ausführen.

Schritt 1. Drücken Sie **F5** zum Ausführen der **Debuggen starten** Befehl. Dieser Befehl erstellt das Projekt und startet den Debugger, starten eine neue Instanz von Visual Studio wird aufgerufen, die **experimentelle Instanz**.

::: moniker range="vs-2017"

Sehen Sie die Wörter **experimentelle Instanz** in der Titelleiste von Visual Studio.

![Titelleiste für die experimentelle Instanz](media/hello-world-exp-instance.png)

::: moniker-end

Schritt 2 Auf der **Tools** Menü mit den **experimentelle Instanz**, klicken Sie auf **Say Hello World!** .

![Endergebnis](media/hello-world-final-result.png)

Daraufhin sollte die Ausgabe von den neuen benutzerdefinierten Befehl, der in diesem Fall das Dialogfeld in der Mitte des Bildschirms das gibt Ihnen die **Hello World!** Vorgang nicht gefunden werden konnte.

## <a name="next-steps"></a>Nächste Schritte

Jetzt wissen Sie die Grundlagen der Arbeit mit Visual Studio-Erweiterbarkeit, hier ist, in denen Sie mehr erfahren können:

* [Mit der Entwicklung von Visual Studio-Erweiterungen beginnen](starting-to-develop-visual-studio-extensions.md) -Beispielen, Lernprogrammen. und veröffentlichen Ihre Erweiterung
* [Neues in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -neuer Erweiterungs-Features in Visual Studio 2017
* [Neues in Visual Studio SDK 2019](whats-new-visual-studio-2019-sdk.md) -neuer Erweiterungs-Features in Visual Studio-2019
* [In Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -erfahren Sie, die Details der Visual Studio-Erweiterbarkeit