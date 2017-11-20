---
title: Erweitern die isolierte Shell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 063a569ff047b3febd2608cb3c1e0003f40f7785
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-isolated-shell"></a>Erweitern Sie die isolierte Shell
Sie können die Visual Studio isolated Shell erweitern, indem Sie ein VSPackage, einer Komponente von Managed Extensibility Framework (MEF) oder ein generischer VSIX-Projekt für die isolierte Shell-Anwendung hinzufügen.  
  
> [!NOTE]
>  Die folgenden Schritte erfordern, dass Sie eine grundlegende isolierten Shell-Anwendung erstellt haben, mit der Visual Studio Shell Isolated-Projektvorlage. Weitere Informationen über diese Projektvorlage finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die VSPackage-Projektvorlage  
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :  
  
1.  Klicken Sie unter **Visual Basic**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Klicken Sie unter **Visual C#-**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C#.  
  
3.  Klicken Sie unter **andere Projekttypen**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C++.  
  
## <a name="adding-a-vspackage"></a>Eine VSPackage hinzufügen  
 Sie können eine VSPackage für die isolierte Shell-Anwendung hinzufügen. Die folgenden Schritte zeigen, wie erstellen, die Befehle im Menü hinzugefügt wird.  
  
#### <a name="to-add-a-new-vspackage"></a>So fügen Sie ein neues VSPackage hinzu  
  
1.  Fügen Sie ein Paket für Visual Studio-Projekt namens `MenuCommandsPackage`.  
  
2.  Auf der **Grundlegende VSPackage-Informationen** Seite des Assistenten festgelegt **Firmenname** auf `Fabrikam` und **VSPackage-Name** auf `FabrikamMenuCommands`. Wählen Sie die **Weiter** Schaltfläche.  
  
3.  Wählen Sie auf der nächsten Seite **Menübefehl** und wählen Sie dann **Weiter**.  
  
4.  Legen Sie auf der nächsten Seite **Befehlsname** auf `Fabrikam Command` und **Befehls-ID** auf `cmdidFabrikamCommand`, und wählen Sie dann **Weiter**.  
  
5.  Auf der **testen Projektoptionen wählen** Seite, deaktivieren Sie die Testoptionen, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
6.  Öffnen Sie im ShellExtensionsVSIX-Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
     Die **Bestand** Abschnitt sollte einen Eintrag für das Projekt VSShellStub.AboutBoxPackage enthalten.  
  
7.  Wählen Sie die **neu** Schaltfläche.  
  
8.  In der **neue Anlage hinzufügen** Fenster, in der **Typ** Liste **Microsoft.VisualStudio.VsPackage**.  
  
9. In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **MenuCommandsPackage**.  
  
10. Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projektmappe neu und Debuggen Sie isolierte Shell.  
  
12. Wählen Sie in der Menüleiste **Tools** klicken Sie dann im Menü **Fabrikam-Befehl**.  
  
     Sollte ein Meldungsfeld angezeigt werden.  
  
13. Debuggen der Anwendung zu beenden.  
  
## <a name="adding-a-mef-component-part"></a>Hinzufügen einer MEF-Komponente  
 Die folgenden Schritte zeigen, wie eine MEF-Komponente zu einer isolierten shellanwendung hinzufügen.  
  
#### <a name="to-add-a-mef-component"></a>So fügen Sie eine MEF-Komponente hinzu  
  
1.  In der **neues Projekt hinzufügen** Dialogfeld unter **Visual C#-**, **Erweiterbarkeit**, verwenden Sie die **Editor Rand** Vorlage Hinzufügen eines Projekts. Nennen Sie es `ShellEditorMargin`.  
  
2.  Öffnen Sie im ShellExtensionsVSIX-Projekt die Datei "Source.Extension.vsixmanifest" in der Entwurfsansicht nicht in der Codeansicht.  
  
3.  In der `Asset` Abschnitt **Inhalt hinzufügen**.  
  
4.  In der **neue Anlage hinzufügen** Fenster, in der **Typ** Liste **Microsoft.VisualStudio.MefComponent**.  
  
5.  In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **ShellEditorMargin**.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Erstellen Sie die Projektmappe neu und Debuggen Sie isolierte Shell.  
  
8.  Öffnen Sie eine Textdatei ein.  
  
     Eine grüne Rand, der die Wörter "Hello World!" enthält. sollte am unteren Rand des Fensters des Text-Datei angezeigt werden.  
  
9. Debuggen der Anwendung zu beenden.  
  
## <a name="adding-a-generic-vsix-project"></a>Hinzufügen eines generischen VSIX-Projekts  
  
#### <a name="to-add-a-generic-vsix-project"></a>Hinzufügen eines generischen VSIX-Projekts  
  
1.  In der **neues Projekt hinzufügen** Dialogfeld unter **Visual C#-**, **Erweiterbarkeit**, verwenden Sie die **VSIXProject** aus, um ein Projekt hinzufügen. Nennen Sie es `EmptyVSIX`.  
  
2.  Öffnen Sie im Projekt ShellExtensionsVSIX die Source.extensions.vsixmanifest-Datei, in der Entwurfsansicht nicht in der Codeansicht.  
  
3.  In der `Assets` Abschnitt **neu**.  
  
4.  In der **neue Anlage hinzufügen** Fenster, in der **Typ** wählen Sie die Art des Inhalts, die Sie hinzufügen möchten.  
  
5.  In **Quelle**, stellen Sie sicher, dass die **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. Wählen Sie im Listenfeld den Namen des VSIX-Projekts ein.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Wenn dieses Projekt kompilierten Code enthält, müssen Sie das Projekt bearbeiten, damit die Assembly in der Ausgabe enthalten ist.  
  
    1.  Entladen Sie das VSIX-Projekt, und öffnen Sie die Projektdatei.  
  
    2.  Im ersten `<PropertyGroup>` blockieren, ändern Sie den Wert der `<CopyBuildOutputToOutputDirectory>` auf `true`.  
  
    3.  Speichern und das Projekt erneut laden.  
  
8.  Erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](walkthrough-creating-a-basic-isolated-shell-application.md)