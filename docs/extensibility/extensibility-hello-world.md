---
title: Hello World-Erweiterung-Lernprogramm | Microsoft-Dokumentation
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7d221526a0fc0214b57eff0c122e526fc09029
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827084"
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

Bevor Sie beginnen, stellen Sie sicher, dass Sie installiert die **Visual Studio-extensionentwicklung** Workload, die die VSIX-Vorlage enthält, Sie benötigen sowie Beispielcode.

> [!NOTE]
> Sie können eine beliebige Edition von Visual Studio (Community, Professional oder Enterprise) zum Erstellen eines Visual Studio-Erweiterbarkeit-Projekts verwenden.

## <a name="create-an-extensibility-project"></a>Erstellen Sie ein Erweiterungsprojekt

Schritt 1. Von der **Datei** Menü klicken Sie auf **neues Projekt**. Geben Sie am unteren Rand des Bildschirms den Namen des Projekts ein.

Schritt 2 Von der **Vorlagen** Menü klicken Sie auf **Visual C#-**, klicken Sie auf **Erweiterbarkeit**, und klicken Sie dann auf **VSIX-Projekt**.

![Neues Projekt](media/hello-world-new-project.png)

Die Seite Erste Schritte und einige Beispielressourcen sollte jetzt angezeigt werden.

Wenn Sie lassen dieses Tutorial, und warten müssen, finden Sie das neue HelloWorld-Projekt auf die **Startseite** in die **zuletzt** Abschnitt.

## <a name="add-a-custom-command"></a>Fügen Sie einen benutzerdefinierten Befehl hinzu

Schritt 1. Wenn Sie das Manifest auswählen, können Sie sehen, welche Optionen für die Instanz, die Metadaten, die Beschreibung und die Version geändert werden.

Schritt 2 Mit der rechten Maustaste in des Projekts (nicht auf die Projektmappe). Klicken Sie im Kontextmenü auf **hinzufügen**, und klicken Sie dann auf **neues Element**.

Schritt 3 Wählen Sie die **Erweiterbarkeit** Abschnitt, und klicken Sie dann auf **benutzerdefinierten Befehls**.

Schritt 4. In der **Namen** Feld am unteren Rand, geben sie einen Namen, z. B. *Command.cs*.

![benutzerdefinierter Befehl](media/hello-world-custom-command.png)

In der neue Befehl aufgeführt ist **Projektmappen-Explorer** unter der **Ressourcen** Branch. Dies ist auch hier finden Sie weitere Dateien, die im Zusammenhang mit der der Befehl, z. B. die PNG und ICO-Dateien, wenn Sie das Bild ändern möchten.

## <a name="modify-the-source-code"></a>Der Quellcode geändert

An diesem Punkt ist die Schaltfläche, die Sie hinzufügen, ziemlich Allgemein. Sie müssen die VSCT-Datei, und die CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* VSCT-Datei ist, in dem Sie können Ihre Befehle umbenennen sowie definieren, in dem sie das System der Visual Studio-Befehl wechseln Sie in. Wenn Sie die VSCT-Datei untersuchen, bemerken Sie viel kommentierten Code, die erklärt, die für jeden Abschnitt des Code-Steuerelemente.

* Die CS-Datei ist, in denen Sie Aktionen wie das Click-Ereignishandler definieren können.

Schritt 1. In **Projektmappen-Explorer**, suchen Sie die VSCT-Datei für den neuen Befehl. In diesem Fall wird Sie aufgerufen *CommandPackage.vsct*.

![Befehl Paket vsct](media/hello-world-command-package-vsct.png)

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

Schritt 3 Wechseln Sie zurück zur **Projektmappen-Explorer** und suchen Sie die *Command.cs* Datei. Ändern Sie die Zeichenfolge `message` für den Befehl `string.Format(..)` zu `Hello World!`.

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Schritt 1. Klicken Sie auf **starten** auf der Symbolleiste. Dies erstellt das Projekt und startet den Debugger, starten eine neue Instanz von Visual Studio wird aufgerufen, die **experimentelle Instanz**.

Sehen Sie die Wörter **experimentelle Instanz** in der Titelleiste von Visual Studio.

![Titelleiste für die experimentelle Instanz](media/hello-world-exp-instance.png)

Schritt 2 Auf der **Tools** Menü mit den **experimentelle Instanz**, klicken Sie auf **Say Hello World!**.

![Endergebnis](media/hello-world-final-result.png)

Daraufhin sollte die Ausgabe von den neuen benutzerdefinierten Befehl, der in diesem Fall das Dialogfeld in der Mitte des Bildschirms das gibt Ihnen die **Hello World!** Vorgang nicht gefunden werden konnte.

## <a name="next-steps"></a>Nächste Schritte

Jetzt wissen Sie die Grundlagen der Arbeit mit Visual Studio-Erweiterbarkeit, hier ist, in denen Sie mehr erfahren können:

* [Mit der Entwicklung von Visual Studio-Erweiterungen beginnen](starting-to-develop-visual-studio-extensions.md) -Beispielen, Lernprogrammen. und veröffentlichen Ihre Erweiterung
* [Neues in Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -neuer Erweiterungs-Features in Visual Studio 2017
* [In Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -erfahren Sie, die Details der Visual Studio-Erweiterbarkeit