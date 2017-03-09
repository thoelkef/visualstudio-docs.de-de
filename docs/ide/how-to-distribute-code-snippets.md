---
title: "Gewusst wie: Verteilen von Codeausschnitten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeausschnitte, Verteilen"
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Verteilen von Codeausschnitten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Codeausschnitte einfach Ihren Freunden geben, und diese können die Ausschnitte mithilfe des Codeausschnitt\-Managers auf ihren Computern installieren.  Wenn Sie jedoch viele Ausschnitte verteilen möchten oder eine breitere Verteilung erforderlich ist, fügen Sie die Ausschnittdatei in eine Visual Studio\-Erweiterung ein, die Benutzer von Visual Studio installieren können.  
  
 Sie müssen das Visual Studio SDK installieren, um Visual Studio\-Erweiterungen zu erstellen.  Suchen Sie unter [Visual Studio 2015 – Downloads](http://www.visualstudio.com/downloads/visual-studio-2015-downloads-vs.aspx) die Version des VSSDK, die Ihrer Visual Studio\-Installation entspricht.  
  
## Einrichten der Erweiterung  
 In diesem Verfahren verwenden wir den "Hello World"\-Codeausschnitt aus [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md).  Wir stellen den SNIPPET\-Text zur Verfügung, damit Sie ihn nicht selbst erstellen müssen.  
  
1.  Erstellen Sie ein neues VSIX\-Projekt namens TestSnippet.  \(**Datei \/ Neu \/ Projekt \/ Visual C\# \(oder Visual Basic \/ Erweiterungen**\)  
  
2.  Fügen Sie im Projekt **TestSnippet** eine neue XML\-Datei hinzu, und nennen Sie sie "VBCodeSnippet.snippet".  Ersetzen Sie den Inhalt durch Folgendes:  
  
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
  
#### Einrichten der Verzeichnisstruktur  
  
1.  Wählen Sie im Projektmappen\-Explorer den Projektknoten, und fügen Sie einen Ordner mit dem Namen hinzu, den der Ausschnitt im Codeausschnitt\-Manager aufweisen soll.  In diesem Fall sollte der Name **HelloWorldVB** sein.  
  
2.  Verschieben Sie die SNIPPET\-Datei in den Ordner **HelloWorldVB**.  
  
3.  Wählen Sie die SNIPPET\-Datei im Projektmappen\-Explorer aus, und stellen Sie sicher, dass im Fenster **Eigenschaften** für die Eigenschaft **Buildvorgang** die Einstellung **Inhalt** ausgewählt ist, für die Eigenschaft **In Ausgabeverzeichnis kopieren** die Einstellung **Immer kopieren** und für die Eigenschaft **Include in VSIX** die Einstellung **TRUE**.  
  
#### Hinzufügen der PKGDEF\-Datei  
  
1.  Fügen Sie dem Ordner **HelloWorldVB** eine Textdatei hinzu, und nennen Sie sie "HelloWorldVB.pkgdef".  Diese Datei wird verwendet, um der Registrierung bestimmte Schlüssel hinzufügen.  In diesem Fall fügt er unter folgendem Pfad einen neuen Schlüssel hinzu:  
  
     HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\Languages\\CodeExpansions\\Basic.  
  
2.  Fügen Sie der Datei die folgenden Zeilen hinzu.  
  
    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  
  
     Wenn Sie diesen Schlüssel untersuchen, sehen Sie, wie verschiedene Sprachen angegeben werden.  
  
3.  Wählen Sie die PKGDEF\-Datei im Projektmappen\-Explorer aus, und stellen Sie sicher, dass im Fenster **Eigenschaften** für die Eigenschaft **Buildvorgang** die Einstellung **Inhalt** ausgewählt ist, für die Eigenschaft **In Ausgabeverzeichnis kopieren** die Einstellung **Immer kopieren** und für die Eigenschaft **Include in VSIX** die Einstellung **TRUE**.  
  
4.  Fügen Sie die PKGDEF\-Datei als Ressource im VSIX\-Manifest hinzu.  Wechseln Sie in der Datei "source.extension.vsixmanifest" zur Registerkarte **Objekte**, und klicken Sie auf **Neu**.  
  
5.  Legen Sie im Dialogfeld **Neue Anlage hinzufügen** für **Typ** die Einstellung **Microsoft.VisualStudio.VsPackage** fest,  für **Typ** die Einstellung **Datei im Dateisystem** und  für **Pfad** die Einstellung **HelloWorldVB.pkgdef** \(sollte in der Dropdownliste angezeigt werden\).  
  
### Testen des Ausschnitts  
  
1.  Jetzt können Sie sicherstellen, dass der Codeausschnitt in der experimentellen Instanz von Visual Studio funktioniert.  Die experimentelle Instanz ist eine zweite Kopie von Visual Studio, die unabhängig von der Instanz ist, die Sie zum Schreiben von Code verwenden.  So können Sie ohne Auswirkungen auf Ihre Entwicklungsumgebung an einer Erweiterung arbeiten.  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging.  Eine zweite Instanz von Visual Studio sollte angezeigt werden.  
  
3.  Wechseln Sie in der experimentellen Instanz zu **Extras \/ Codeausschnitt\-Manager**, und wählen Sie für **Sprache** die Einstellung **Basic**.  "HelloWorldVB" sollte als einer der Ordner angezeigt werden, und wenn Sie den Ordner erweitern, sollten Sie den Ausschnitt "HelloWorldVB" sehen.  
  
4.  Speichern Sie den Ausschnitt.  Öffnen Sie in der experimentellen Instanz ein Visual Basic\-Projekt, und öffnen Sie dann eine der Codedateien.  Platzieren Sie den Cursor an einer beliebigen Stelle im Code, klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü den Befehl **Ausschnitt einfügen**.  
  
5.  "HelloWorldVB" sollte als einer der Ordner angezeigt werden.  Doppelklicken Sie darauf.  Es sollte ein Popupfenster **Ausschnitt einfügen: HellowWorldVB \>** mit der Dropdownliste **HelloWorldVB** angezeigt werden.  Klicken Sie auf die Dropdownliste "HelloWorldVB".  Sie sollten sehen, dass der Datei die folgende Zeile hinzugefügt wurde:  
  
    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  
  
## Siehe auch  
 [Codeausschnitte](../ide/code-snippets.md)