---
title: Erweitern der isolierten Shell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840985"
---
# <a name="extending-the-isolated-shell"></a>Erweitern der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die isolierte Visual Studio-Shell erweitern, indem Sie der isolierten Shellanwendung ein VSPackage, einen Managed Extensibility Framework-Komponenten Teil (MEF) oder ein generisches VSIX-Projekt hinzufügen.  
  
> [!NOTE]
> In den folgenden Schritten wird vorausgesetzt, dass Sie eine grundlegende isolierte Shell-Anwendung mithilfe der Projektvorlage von Visual Studio Shell (isoliert) erstellt haben. Weitere Informationen zu dieser Projektvorlage finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Stellen für die VSPackage-Projektvorlage  
 Die VSPackage-Projektvorlage finden Sie an drei verschiedenen Stellen im Dialogfeld **Neues Projekt** :  
  
1. Unter **Visual Basic**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist Visual Basic.  
  
2. Unter **Visual c#**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C#.  
  
3. Unter **andere Projekttypen**, **Erweiterbarkeit**. Die Standardsprache des Projekts ist C++.  
  
## <a name="adding-a-vspackage"></a>Hinzufügen eines VSPackages  
 Sie können ihrer isolierten Shellanwendung ein VSPackage hinzufügen. Die folgenden Schritte zeigen, wie Sie eine erstellen, die Menübefehle hinzufügt.  
  
#### <a name="to-add-a-new-vspackage"></a>So fügen Sie ein neues VSPackage hinzu  
  
1. Fügen Sie ein Visual Studio-Paket Projekt namens hinzu `MenuCommandsPackage` .  
  
2. Legen Sie auf der Seite **grundlegende VSPackage-Informationen** des Assistenten für **Unternehmens Name** `Fabrikam` und **VSPackage Name** den Wert fest `FabrikamMenuCommands` . Klicken Sie auf **Weiter**.  
  
3. Wählen Sie auf der nächsten Seite **Menübefehl** aus, und klicken Sie dann auf **weiter**.  
  
4. Legen Sie auf der nächsten Seite **Befehls Name** `Fabrikam Command` und **Befehls-ID** auf fest `cmdidFabrikamCommand` , und klicken Sie dann auf **weiter**.  
  
5. Deaktivieren Sie auf der Seite Optionen für das **Testprojekt auswählen** die Test Optionen, und wählen Sie dann die Schaltfläche **Fertig** stellen aus.  
  
6. Öffnen Sie im shellextensionsvsix-Projekt die Datei "Source. Extension. vsixmanifest".  
  
     Der Abschnitt **Assets** sollte einen Eintrag für das Projekt vsshellstub. aboutboxpackage enthalten.  
  
7. Wählen Sie die Schaltfläche **neu** aus.  
  
8. Wählen Sie im Fenster **Neues Objekt hinzufügen** in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. VSPackage**aus.  
  
9. Stellen Sie in der Liste **Quelle** sicher, dass **ein Projekt in der aktuellen Projekt** Mappe ausgewählt ist. Wählen Sie im Listenfeld **Projekt** den Text **menucommandspackage**aus.  
  
10. Speichern und schließen Sie die Datei.  
  
11. Erstellen Sie die Projekt Mappe neu, und starten Sie das Debugging der isolierten Shell  
  
12. Klicken **Sie in der Menüleiste** auf Extras, und klicken Sie dann auf **Fabrikam-Befehl**.  
  
     Ein Meldungs Feld sollte angezeigt werden.  
  
13. Beendet das Debuggen der Anwendung.  
  
## <a name="adding-a-mef-component-part"></a>Hinzufügen eines MEF-Komponenten Teils  
 Die folgenden Schritte zeigen, wie Sie Ihrer isolierten Shellanwendung einen MEF-Komponenten Teil hinzufügen.  
  
#### <a name="to-add-a-mef-component"></a>So fügen Sie eine MEF-Komponente hinzu  
  
1. Verwenden Sie im Dialogfeld **Neues Projekt hinzufügen** unter **Visual c#**, **Erweiterbarkeit**, die Vorlage für den **Editor Rand** , um ein Projekt hinzuzufügen. Vergeben Sie den Namen `ShellEditorMargin`.  
  
2. Öffnen Sie im shellextensionsvsix-Projekt die Datei "Source. Extension. vsixmanifest" im Designansicht, nicht in der Code Ansicht.  
  
3. `Asset`Wählen Sie im Abschnitt **Inhalt hinzufügen**aus.  
  
4. Wählen Sie im Fenster **Neues Objekt hinzufügen** in der Liste **Typ** den Eintrag **Microsoft. VisualStudio. MEFComponent**aus.  
  
5. Stellen Sie in der Liste **Quelle** sicher, dass **ein Projekt in der aktuellen Projekt** Mappe ausgewählt ist. Wählen Sie im Listenfeld **Projekt** den Text **shelleditor Margin**aus.  
  
6. Speichern und schließen Sie die Datei.  
  
7. Erstellen Sie die Projekt Mappe neu, und starten Sie das Debugging der isolierten Shell  
  
8. Öffnen Sie eine Textdatei.  
  
     Ein grüner Rand, der die Wörter "Hello World!" enthält. sollte am unteren Rand des Textdatei-Fensters angezeigt werden.  
  
9. Beendet das Debuggen der Anwendung.  
  
## <a name="adding-a-generic-vsix-project"></a>Hinzufügen eines generischen VSIX-Projekts  
  
#### <a name="to-add-a-generic-vsix-project"></a>So fügen Sie ein generisches VSIX-Projekt hinzu  
  
1. Verwenden Sie im Dialogfeld **Neues Projekt hinzufügen** unter **Visual c#**( **Erweiterbarkeit**) die Vorlage **VSIXProject** , um ein Projekt hinzuzufügen. Vergeben Sie den Namen `EmptyVSIX`.  
  
2. Öffnen Sie im shellextensionsvsix-Projekt die Datei "Source. Extensions. vsixmanifest" im Designansicht, nicht in der Code Ansicht.  
  
3. `Assets`Wählen Sie im Abschnitt **neu**aus.  
  
4. Wählen Sie im Fenster **Neues Objekt hinzufügen** in der Liste **Typ** die Art des Inhalts aus, den Sie hinzufügen möchten.  
  
5. Stellen Sie sicher, dass unter **Quelle**die Option **ein Projekt in der aktuellen Projekt** Mappe ausgewählt ist. Wählen Sie im Listenfeld den Namen des VSIX-Projekts aus.  
  
6. Speichern und schließen Sie die Datei.  
  
7. Wenn dieses Projekt kompilierten Code enthält, müssen Sie das Projekt so bearbeiten, dass die Assembly in der Ausgabe enthalten ist.  
  
    1. Entladen Sie das VSIX-Projekt, und öffnen Sie die Projektdatei.  
  
    2. Ändern Sie im ersten- `<PropertyGroup>` Block den Wert von `<CopyBuildOutputToOutputDirectory>` in `true` .  
  
    3. Speichern und laden Sie das Projekt erneut.  
  
8. Erstellen Sie das Projekt, und führen Sie es aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
