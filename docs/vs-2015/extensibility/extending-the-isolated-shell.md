---
title: Erweitern der Isolated Shell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec39a36c3f600905543e2d58db7228324f63d97e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520401"
---
# <a name="extending-the-isolated-shell"></a>Erweitern der Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erweitern der Isolated Shell](https://docs.microsoft.com/visualstudio/extensibility/extending-the-isolated-shell).  
  
Sie können die Visual Studio isolierte Shell erweitern, indem Ihre isolated Shell-Anwendung ein VSPackage, einer Komponente des Managed Extensibility Framework (MEF) oder ein generischer VSIX-Projekt hinzugefügt.  
  
> [!NOTE]
>  Die folgenden Schritte erfordern, dass Sie eine grundlegenden isolated Shell-Anwendung unter Verwendung der isolierten Visual Studio Shell-Projektvorlage erstellt haben. Weitere Informationen zu dieser Projektvorlage, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Speicherorte für die VSPackage-Projektvorlage  
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :  
  
1.  Klicken Sie unter **Visual Basic**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist Visual Basic.  
  
2.  Klicken Sie unter **Visual C#-**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C#.  
  
3.  Klicken Sie unter **anderen Projekttypen**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C++.  
  
## <a name="adding-a-vspackage"></a>Hinzufügen von einem VSPackage  
 Sie können eine VSPackage für die isolierte Shell-Anwendung hinzufügen. Die folgenden Schritte zeigen, wie Sie eine erstellen, die Befehle im Menü hinzugefügt wird.  
  
#### <a name="to-add-a-new-vspackage"></a>Hinzufügen ein neues VSPackage  
  
1.  Fügen Sie ein Visual Studio-Paket-Projekt mit dem Namen `MenuCommandsPackage`.  
  
2.  Auf der **grundlegende Informationen zum VSPackage** Seite des Assistenten festgelegt **Firmenname** zu `Fabrikam` und **VSPackage-Name** zu `FabrikamMenuCommands`. Klicken Sie auf **Weiter**.  
  
3.  Wählen Sie auf der nächsten Seite **Menübefehl** und wählen Sie dann **Weiter**.  
  
4.  Legen Sie auf der nächsten Seite **Befehlsnamen** zu `Fabrikam Command` und **Befehls-ID** zu `cmdidFabrikamCommand`, und wählen Sie dann **Weiter**.  
  
5.  Auf der **testen Projektoptionen wählen** Seite, deaktivieren Sie die Testoptionen, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
6.  Öffnen Sie im ShellExtensionsVSIX-Projekt die Datei "Source.Extension.vsixmanifest" ein.  
  
     Die **Assets** Abschnitt sollte einen Eintrag für das Projekt VSShellStub.AboutBoxPackage enthalten.  
  
7.  Wählen Sie die **neu** Schaltfläche.  
  
8.  In der **neue Anlage hinzufügen** Fenster in der **Typ** Liste **"Microsoft.VisualStudio.VSPackage"**.  
  
9. In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **MenuCommandsPackage**.  
  
10. Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projektmappe neu, und starten Sie das Debuggen der isolated Shells.  
  
12. Wählen Sie auf der Menüleiste **Tools** Menü **Fabrikam-Befehl**.  
  
     Es sollte ein Meldungsfeld angezeigt.  
  
13. Beenden des Debuggens der Anwendungs.  
  
## <a name="adding-a-mef-component-part"></a>Hinzufügen einer MEF-Komponente  
 Die folgenden Schritte zeigen, wie Ihre isolated Shell-Anwendung eine MEF-Komponente hinzugefügt wird.  
  
#### <a name="to-add-a-mef-component"></a>Hinzufügen eine MEF-Komponente  
  
1.  In der **neues Projekt hinzufügen** Dialogfeld **Visual C#-**, **Erweiterbarkeit**, verwenden Sie die **Rand des Editors** Vorlage zum Hinzufügen eines Projekts. Nennen Sie es `ShellEditorMargin`.  
  
2.  Öffnen Sie die Datei "Source.Extension.vsixmanifest" in der Entwurfsansicht, nicht in der Codeansicht ShellExtensionsVSIX im Projekt.  
  
3.  In der `Asset` Abschnitt **Inhalt hinzufügen**.  
  
4.  In der **neue Anlage hinzufügen** Fenster in der **Typ** Liste **Microsoft.VisualStudio.MefComponent**.  
  
5.  In der **Quelle** auflisten, stellen Sie sicher, dass **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. In der **Projekt** wählen Sie im Listenfeld **ShellEditorMargin**.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Erstellen Sie die Projektmappe neu, und starten Sie das Debuggen der isolated Shells.  
  
8.  Öffnen Sie eine Textdatei ein.  
  
     Ein grünes Rand, der die Wörter "Hello World!" enthält. sollte am unteren Rand des Fensters des Text-Datei angezeigt werden.  
  
9. Beenden des Debuggens der Anwendungs.  
  
## <a name="adding-a-generic-vsix-project"></a>Hinzufügen eines generischen VSIX-Projekts  
  
#### <a name="to-add-a-generic-vsix-project"></a>Zum Hinzufügen eines generischen VSIX-Projekts  
  
1.  In der **neues Projekt hinzufügen** Dialogfeld **Visual C#-**, **Erweiterbarkeit**, verwenden Sie die **VSIXProject** Vorlage zum Hinzufügen eines Projekts. Nennen Sie es `EmptyVSIX`.  
  
2.  Öffnen Sie im Projekt ShellExtensionsVSIX die Source.extensions.vsixmanifest-Datei in der Entwurfsansicht nicht in der Codeansicht.  
  
3.  In der `Assets` Abschnitt **neu**.  
  
4.  In der **neue Anlage hinzufügen** Fenster in der **Typ** wählen die Art des Inhalts, die Sie hinzufügen möchten.  
  
5.  In **Quelle**, stellen Sie sicher, dass die **ein Projekt in der aktuellen Projektmappe** ausgewählt ist. Wählen Sie im Listenfeld den Namen des VSIX-Projekts ein.  
  
6.  Speichern und schließen Sie die Datei.  
  
7.  Wenn dieses Projekt kompilierten Code enthält, müssen Sie das Projekt bearbeiten, damit die Assembly in der Ausgabe enthalten ist.  
  
    1.  Entladen Sie das VSIX-Projekt, und öffnen Sie die Projektdatei.  
  
    2.  In der ersten `<PropertyGroup>` blockieren, ändern Sie den Wert der `<CopyBuildOutputToOutputDirectory>` zu `true`.  
  
    3.  Speichern Sie und Laden Sie das Projekt.  
  
8.  Erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

