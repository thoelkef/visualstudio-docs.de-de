---
title: "Erweitern Sie die isolierte Shell | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell, isolierten Modus"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Erweitern Sie die isolierte Shell
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Visual Studio isolated Shell erweitern, indem der isolierte Shell\-Anwendung ein VSPackage, einer Komponente von Managed Extensibility Framework \(MEF\) oder ein generisches VSIX\-Projekt hinzuzufügen.  
  
> [!NOTE]
>  Die folgenden Schritte erfordern, dass Sie eine grundlegende isolierte Shell\-Anwendung mithilfe der Visual Studio Shell Isolated Projektvorlage erstellt haben. Weitere Informationen über diese Projektvorlage finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## Speicherorte für die VSPackage\-Projektvorlage  
 Die VSPackage\-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt**:  
  
1.  Klicken Sie unter **Visual Basic**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Klicken Sie unter **Visual C\#\-**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C\#.  
  
3.  Klicken Sie unter **Andere Projekttypen**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C\+\+.  
  
## Hinzufügen eines VSPackages  
 Sie können ein VSPackage der isolierte Shell\-Anwendung hinzufügen. Die folgenden Schritte zeigen, wie erstellen, die Befehle im Menü hinzugefügt wird.  
  
#### Hinzufügen ein neues VSPackage  
  
1.  Fügen Sie ein Visual Studio\-Paket\-Projekt mit dem Namen `MenuCommandsPackage`.  
  
2.  Auf der **Grundlegende VSPackage\-Informationen** Seite des Assistenten festgelegt **Firmenname**`Fabrikam` und **VSPackage\-Namen** auf `FabrikamMenuCommands`. Wählen Sie die Schaltfläche **Weiter** aus.  
  
3.  Wählen Sie auf der nächsten Seite **Menübefehl** und wählen Sie dann **Weiter**.  
  
4.  Legen Sie auf der nächsten Seite **Befehlsnamen**`Fabrikam Command` und **Befehls\-ID** auf `cmdidFabrikamCommand`, und wählen Sie dann **Weiter**.  
  
5.  Auf der **Testen Projektoptionen wählen** Seite, deaktivieren Sie die Testoptionen, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
6.  Öffnen Sie im ShellExtensionsVSIX\-Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
     Die **Elemente** Abschnitt sollte einen Eintrag für das Projekt VSShellStub.AboutBoxPackage enthalten.  
  
7.  Wählen Sie die Schaltfläche **Neu** aus.  
  
8.  In der **neue Anlage hinzufügen** Fenster in der **Typ** Liste **Microsoft.VisualStudio.VsPackage**.  
  
9. In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **MenuCommandsPackage**.  
  
10. Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Lösung Debuggen und die isolierte Shell.  
  
12. Wählen Sie auf der Menüleiste **Tools** Menü **Fabrikam\-Befehl**.  
  
     Es sollte ein Meldungsfeld angezeigt.  
  
13. Beenden Sie die Anwendung debuggen.  
  
## Hinzufügen einer MEF\-Komponente  
 Die folgenden Schritte zeigen, wie Ihre Anwendung für isolierte Shells eine MEF\-Komponente hinzugefügt wird.  
  
#### Hinzufügen eine MEF\-Komponente  
  
1.  In der **Neues Projekt hinzufügen** Dialogfeld **Visual C\#\-**, **Erweiterbarkeit**, verwenden Sie die **Rand\-Editor** Vorlage zum Hinzufügen eines Projekts. Nennen Sie es `ShellEditorMargin`.  
  
2.  Öffnen Sie im ShellExtensionsVSIX\-Projekt die Datei "Source.extension.vsixmanifest" in der Entwurfsansicht nicht in der Codeansicht.  
  
3.  In der `Asset` Abschnitt **Inhalt hinzufügen**.  
  
4.  In der **neue Anlage hinzufügen** Fenster in der **Typ** Liste **Microsoft.VisualStudio.MefComponent**.  
  
5.  In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **ShellEditorMargin**.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Erstellen Sie die Lösung Debuggen und die isolierte Shell.  
  
8.  Öffnen Sie eine Textdatei.  
  
     Ein grüner Rand, der die Wörter "Hello World\!" sollte am unteren Rand des Textfensters\-Datei angezeigt werden.  
  
9. Beenden Sie die Anwendung debuggen.  
  
## Hinzufügen eines generischen VSIX\-Projekts  
  
#### Ein generisches VSIX\-Projekt hinzufügen  
  
1.  In der **Neues Projekt hinzufügen** Dialogfeld **Visual C\#\-**, **Erweiterbarkeit**, verwenden Sie die **VSIXProject** Vorlage zum Hinzufügen eines Projekts. Nennen Sie es `EmptyVSIX`.  
  
2.  Öffnen Sie im Projekt ShellExtensionsVSIX die Source.extensions.vsixmanifest\-Datei in der Entwurfsansicht nicht in der Codeansicht.  
  
3.  In der `Assets` Abschnitt **Neu**.  
  
4.  In der **neue Anlage hinzufügen** Fenster in der **Typ** wählen Sie die Art der Inhalte, die Sie hinzufügen möchten.  
  
5.  In **Quelle**, stellen Sie sicher, dass die **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. Wählen Sie im Listenfeld den Namen der VSIX\-Projekt.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Wenn dieses Projekt kompilierten Code enthält, müssen Sie das Projekt bearbeiten, damit die Assembly in der Ausgabe enthalten ist.  
  
    1.  Entladen Sie das VSIX\-Projekt, und öffnen Sie die Projektdatei.  
  
    2.  In der ersten `<PropertyGroup>` blockieren, ändern Sie den Wert von `<CopyBuildOutputToOutputDirectory>` auf `true`.  
  
    3.  Speichern und das Projekt erneut laden.  
  
8.  Erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)