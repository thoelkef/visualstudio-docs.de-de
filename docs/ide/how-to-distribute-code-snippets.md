---
title: 'Vorgehensweise: Verteilen von Codeausschnitten'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 85500cfb5d8977c1e06ac925a44ba20bf3144d31
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280310"
---
# <a name="how-to-distribute-code-snippets"></a>Vorgehensweise: Verteilen von Codeausschnitten

Sie können Codeausschnitte Ihren Freunden geben und diese können die Ausschnitte mithilfe des Codeausschnitt-Managers auf ihren Computern installieren. Wenn Sie jedoch viele Ausschnitte verteilen möchten oder eine breitere Verteilung erforderlich ist, fügen Sie die Ausschnittdatei in eine Visual Studio-Erweiterung ein, die Benutzer von Visual Studio installieren können.

Sie müssen das Visual Studio SDK installieren, um Visual Studio-Erweiterungen zu erstellen. Unter [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) finden Sie die Version des Visual Studio SDK, die zu Ihrer Installation von Visual Studio passt.

## <a name="set-up-the-extension"></a>Einrichten der Erweiterung

In diesem Verfahren verwenden wir den „Hello World“-Codeausschnitt aus [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md). Wir stellen den *SNIPPET*-Text zur Verfügung, damit Sie ihn nicht selbst erstellen müssen.

1.  Erstellen Sie ein neues VSIX-Projekt namens **TestSnippet**. (**Datei** > **Neu** > **Projekt** > **Visual C# (oder Visual Basic)** > **Erweiterungen**)

2.  Fügen Sie im Projekt **TestSnippet** eine neue XML-Datei hinzu, und nennen Sie sie *VBCodeSnippet.snippet*. Ersetzen Sie den Inhalt durch Folgendes:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeSnippets
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
      <CodeSnippet Format="1.0.0">
        <Header>
          <Title>Hello World VB</Title>
          <Shortcut>HelloWorld</Shortcut>
          <Description>Inserts code</Description>
          <Author>MSIT</Author>
          <SnippetTypes>
            <SnippetType>Expansion</SnippetType>
            <SnippetType>SurroundsWith</SnippetType>
          </SnippetTypes>
        </Header>
        <Snippet>
          <Code Language="VB">
            <![CDATA[Console.WriteLine("Hello, World!")]]>
          </Code>
        </Snippet>
      </CodeSnippet>
    </CodeSnippets>
    ```

### <a name="set-up-the-directory-structure"></a>Einrichten der Verzeichnisstruktur

1.  Klicken Sie im **Projektmappen-Explorer** auf den Projektknoten, und fügen Sie einen Ordner mit dem Namen hinzu, den der Ausschnitt im **Codeausschnitt-Manager** aufweisen soll. In diesem Fall sollte der Name **HelloWorldVB** lauten.

2.  Verschieben Sie die *SNIPPET*-Datei in den Ordner *HelloWorldVB*.

3.  Klicken Sie im **Projektmappen**-Explorer auf die *SNIPPET*-Datei, und stellen Sie sicher, dass im Fenster **Eigenschaften** für die Eigenschaft **Buildvorgang** die Einstellung **Inhalt**, für die Eigenschaft **In Ausgabeverzeichnis kopieren** die Einstellung **Immer kopieren** und für die Eigenschaft **Include in VSIX** (In VSIX einbeziehen) die Einstellung **TRUE** ausgewählt ist.

### <a name="add-the-pkgdef-file"></a>Hinzufügen der PKGDEF-Datei

1.  Fügen Sie dem Ordner *HelloWorldVB* eine Textdatei hinzu, und nennen Sie sie *HelloWorldVB.pkgdef*. Diese Datei wird verwendet, um der Registrierung bestimmte Schlüssel hinzufügen. In diesem Fall fügt er unter folgendem Pfad einen neuen Schlüssel hinzu:

     `HKCU\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic`

2.  Fügen Sie der Datei die folgenden Zeilen hinzu.

    ```txt
    // Visual Basic
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]
    "HelloWorldVB"="$PackageFolder$"
    ```

    Wenn Sie diesen Schlüssel untersuchen, sehen Sie, wie verschiedene Sprachen angegeben werden.

3.  Klicken Sie im **Projektmappen-Explorer** auf die *PKGDEF*-Datei, und stellen Sie sicher, dass im Fenster **Eigenschaften** für die Eigenschaft **Buildvorgang** die Einstellung **Inhalt**, für die Eigenschaft **In Ausgabeverzeichnis kopieren** die Einstellung **Immer kopieren** und für die Eigenschaft **Include in VSIX** (In VSIX einbeziehen) die Einstellung **TRUE** ausgewählt ist.

4.  Fügen Sie dem VSIX-Manifest die *PKGDEF*-Datei als Ressource hinzu. Wechseln Sie in der Datei *source.extension.vsixmanifest* zur Registerkarte **Objekte**, und klicken Sie auf **Neu**.

5.  Legen Sie im Dialogfeld **Neue Anlage hinzufügen** für **Typ** die Einstellung **Microsoft.VisualStudio.VsPackage** fest, für **Quelle** die Einstellung **Datei im Dateisystem** und für **Pfad** die Einstellung **HelloWorldVB.pkgdef** (sollte in der Dropdownliste angezeigt werden).

### <a name="test-the-snippet"></a>Testen des Ausschnitts

1.  Jetzt können Sie sicherstellen, dass der Codeausschnitt in der experimentellen Instanz von Visual Studio funktioniert. Die experimentelle Instanz ist eine zweite Kopie von Visual Studio, die unabhängig von der Instanz ist, die Sie zum Schreiben von Code verwenden. So können Sie ohne Auswirkungen auf Ihre Entwicklungsumgebung an einer Erweiterung arbeiten.

2.  Erstellen Sie das Projekt, und starten Sie das Debugging. Eine zweite Instanz von Visual Studio sollte angezeigt werden.

3.  Wechseln Sie in der experimentellen Instanz zu **Extras > Codeausschnitt-Manager**, und wählen Sie für **Sprache** die Einstellung **Basic** aus. *HelloWorldVB* sollte als einer der Ordner angezeigt werden, und wenn Sie den Ordner erweitern, sollten Sie den Ausschnitt *HelloWorldVB* sehen.

4.  Speichern Sie den Ausschnitt. Öffnen Sie in der experimentellen Instanz ein Visual Basic-Projekt, und öffnen Sie dann eine der Codedateien. Platzieren Sie den Cursor an einer beliebigen Stelle im Code, klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü den Befehl **Ausschnitt einfügen**.

5.  *HelloWorldVB* sollte als einer der Ordner angezeigt werden. Doppelklicken Sie darauf. Es sollte ein Popupfenster **Ausschnitt einfügen: HelloWorldVB >** mit der Dropdownliste **HelloWorldVB** angezeigt werden. Klicken Sie auf die Dropdownliste **HelloWorldVB**. Sie sollten sehen, dass der Datei die folgende Zeile hinzugefügt wurde:

    ```vb
    Console.WriteLine("Hello, World!")
    ```

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte](../ide/code-snippets.md)