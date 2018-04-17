---
title: Hello World | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c531d8acddfebcd2656d6dca05b95244f54ec01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-your-first-extension-hello-world"></a>Erstellen die erste Erweiterung: Hello World

In diesem Hello World-Beispiel führt Sie durch die erste Erweiterung für Visual Studio erstellen. In diesem Lernprogramm erfahren Sie, wie Visual Studio einen neuen Befehl hinzugefügt.

Im Prozess, erfahren Sie, wie Sie:

* **[Erstellen Sie ein Erweiterungsprojekt](#create-an-extensibility-project)**
* **[Fügen Sie einen benutzerdefinierten Befehl hinzu](#add-a-custom-command)**
* **[Ändern Sie den Quellcode](#modify-the-source-code)**
* **[Führen Sie es](#run-it)**

In diesem Beispiel verwenden Visual C#-Sie eine benutzerdefinierte Schaltfläche mit dem Namen "Sagen Hello World!" hinzufügen Das sieht wie folgt:

![Hello World-Befehl](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie beginnen, stellen Sie sicher, dass Sie installiert die **Development für Visual Studio-Erweiterung** arbeitsauslastung, die die VSIX-Vorlage enthält, Sie benötigen und Beispielcode.

Hinweis: Sie können eine beliebige Version von Visual Studio (Community, Professional oder Enterprise) zum Erstellen eines Projekts von Visual Studio-Erweiterbarkeit.

## <a name="create-an-extensibility-project"></a>Erstellen Sie ein Erweiterungsprojekt

Schritt 1. Aus der **Datei** Menü klicken Sie auf **neues Projekt**. Am unteren Rand des Bildschirms können Sie den Namen des Projekts eingeben.

Schritt 2 Aus der **Vorlagen** Menü klicken Sie auf **Visual C#-**, klicken Sie auf **Erweiterbarkeit**, und klicken Sie dann auf **VSIX-Projekt**.

![Neues Projekt](media/hello-world-new-project.png)

Die Seite "Erste Schritte" und einige Beispielressourcen sollte jetzt angezeigt werden.

Wenn Sie dieses Lernprogramm lassen und zurückkehren, um es müssen, finden Sie das neue HelloWorld-Projekt auf die **Startseite** in der **zuletzt** Abschnitt.

## <a name="add-a-custom-command"></a>Fügen Sie einen benutzerdefinierten Befehl hinzu

Schritt 1. Wenn Sie das Manifest auswählen, können Sie sehen, welche Optionen Objekteigenschaft, für die Instanz, die Metadaten, die Beschreibung und die Version sind.

Schritt 2 Mit der rechten Maustaste in des Projekts (nicht die Projektmappe). Klicken Sie im Kontextmenü auf **hinzufügen**, und klicken Sie dann auf **Benutzersteuerelement**.

Schritt 3 Wechseln Sie zurück zu den **Erweiterbarkeit** Abschnitt, und klicken Sie dann auf **benutzerdefinierte Befehl**.

Schritt 4. In der **Namen** Eigenschaftsfeld, geben sie einen Namen, z. B. Command.cs.

![benutzerdefinierte Befehl](media/hello-world-custom-command.png)

In der neue Befehl aufgelistet werden die **Projektmappen-Explorer** unter der **Ressourcen** Verzweigung. Dies ist auch hier finden Sie weitere Dateien, die im Zusammenhang mit dem Befehl, z. B. die PNG und ICO-Dateien, wenn Sie das Bild ändern möchten.

## <a name="modify-the-source-code"></a>Ändern Sie den Quellcode

An diesem Punkt ist die Schaltfläche, die Sie hinzufügen, ziemlich generisch. Sie müssen die VSCT-Datei, und die CS-Datei ändern, wenn Sie Änderungen vornehmen möchten.

* Die VSCT-Datei ist, in dem Sie können Ihre Befehle umbenennen, sowie definieren, in dem sie in der Visual Studio-Befehlssystem eingefügt werden. Wie Sie die VSCT-Datei durchsuchen, bemerken Sie viele kommentierten Code, die erläutert, welche jedes Abschnitts des Code-Steuerelemente.

* Die CS-Datei ist, in denen Sie Aktionen wie das Click-Ereignishandler definieren können.

Schritt 1. In **Projektmappen-Explorer**, suchen Sie die VSCT-Datei für den neuen Befehl. In diesem Fall wird es CommandPackage.vsct aufgerufen.

![Befehl Paket vsct](media/hello-world-command-package-vsct.png)

Schritt 2 Ändern der `ButtonText` Parameter "Sagen: Hello World!"

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

Schritt 3 Wechseln Sie zurück zum **Projektmappen-Explorer** und suchen Sie die Datei Command.cs. Ändern Sie die Zeichenfolge `message` für den Befehl `string.Format(..)` um "Hello World!"

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

Stellen Sie sicher, dass die Änderungen an den einzelnen Dateien zu speichern.

## <a name="run-it"></a>Führen Sie es

Sie können jetzt den Quellcode in der experimentellen Instanz von Visual Studio ausführen.

Schritt 1. Klicken Sie auf **starten** auf der Symbolleiste. Dadurch erstellen Sie das Projekt und starten Sie den Debugger, starten eine neue Instanz von Visual Studio aufgerufen, wird die **experimentelle Instanz**.

Sie sehen, dass die Wörter "Experimentelle Instanz" in der Visual Studio-Titelleiste.

![Titelleiste experimentelle Instanz](media/hello-world-exp-instance.png)

Schritt 2 Auf der **Tools** Menü der **experimentelle Instanz**, klicken Sie auf **Say Hello World!**.

![Endergebnis](media/hello-world-final-result.png)

Sie sollten die Ausgabe aus den neuen benutzerdefinierten-Befehl aus, in diesem Fall das Dialogfeld "in der Mitte des Bildschirms angezeigt, die Sie die"Hello World!"enthält Vorgang nicht gefunden werden konnte.

## <a name="next-steps"></a>Nächste Schritte

Nun, dass Sie wissen, dass die Grundlagen der Arbeit mit Visual Studio-Erweiterbarkeit, sieht aus, in denen Sie mehr erfahren können:

* [Starten Visual Studio-Erweiterungen entwickeln](starting-to-develop-visual-studio-extensions.md) -Beispiele, Lernprogramme. und veröffentlichen die Erweiterung.
* [Neuigkeiten in der Visual Studio-SDK 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -neue Erweiterungsfunktionen in Visual Studio 2017
* [In Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -erfahren Sie, die Details der Visual Studio-Erweiterbarkeit