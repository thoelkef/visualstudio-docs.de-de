---
redirect_url: shell/customizing-the-isolated-shell
title: Anpassen der isolierten Shells | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35aab40dbacd814dcec281ff1f3dd529b29d4424
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="customizing-the-isolated-shell"></a>Anpassen der isolierten Shells
Sie können Ihre Visual Studio isolated Shell-Anwendung anpassen, indem verschiedene Aspekte der Visual Studio-Benutzeroberfläche zu ändern und die Befehle und Funktionen, die in der speziellen Anwendung enthalten.  
  
## <a name="using-the-applicationpkgdef-file"></a>Mithilfe der Datei Application.pkgdef  
 Die vorlagenlösung isolierte Shell umfasst eine *SolutionName*. Application.PKGDEF-Datei, die Ihnen ermöglicht, ändern Sie die folgenden Funktionen:  
  
##### <a name="the-application-title"></a>Der Titel der Anwendung  
 Sie können anpassen, dass der Titel der Anwendung, der der Name, der in der Titelleiste der Anwendung angezeigt wird ist, durch Ändern des Werts der "AppName" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Wenn Sie nicht möchten, wird der Titel der Anwendung das Projekt angezeigt, die derzeit geladen ist, ändern Sie den Wert der Zeile "ShowHierarchyRootInTitle" in der *SolutionName*. Application.PKGDEF Datei aus DWORD: 00000001 DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Symbol "Anwendung"  
 Sie können das Anwendungssymbol anpassen, das welche das Symbol entspricht, das durch den Namen der Anwendung in der Titelleiste der Anwendung angezeigt wird. Kopieren Sie ein anderes Symbol auf das Symbol "-Verzeichnis. In **Projektmappen-Explorer**, das Symbol "hinzufügen" auf den Ordner der Ressource. Klicken Sie dann öffnen Sie die VSShellStub.rc-Datei zu, und Ersetzen Sie den Wert des IDI_STUBPROGRAM mit dem Namen des neuen Symbols. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Das Befehlszeilen-logo  
 Sie können anpassen, das Befehlszeile-Logo, d. h. der Text, der angezeigt wird, wenn die Anwendung über die Befehlszeile gestartet wird, durch Ändern des Werts der Zeile "CommandLineLogo" in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierten Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Der Name des Unterordners Benutzer Dateien  
 Sie können den Namen des Ordners die Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der Zeile "UserFilesSubFolderName" in ändern *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Der Titel des Strukturknotens Lösung klicken Sie im Dialogfeld "Neues Projekt"  
 Sie können den Titel der den Projektmappenknoten, klicken Sie im Dialogfeld "Neues Projekt" anpassen, durch Ändern des Werts der Zeile "NewProjDlgSlnTreeNodeTitle" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Klicken Sie im Dialogfeld "Neues Projekt" der installierten Vorlagen-header  
 Kann, ändern Sie den installierten Vorlagen-Header, klicken Sie im Dialogfeld "Neues Projekt" durch Ändern des Werts der Zeile "NewProjDlgInstalledTemplatesHdr" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Ob verschiedene Dateien standardmäßig ausblenden  
 Sie können angeben, ob verschiedene Dateien standardmäßig ausblenden, durch Ändern des Werts der Zeile "HideMiscellaneousFilesByDefault" in der *SolutionName*. Application.PKGDEF-Datei. Um verschiedene Dateien auszublenden, legen Sie den Wert `dword:00000001`, und um die Dateien anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Ob das Fenster "Ausgabe" deaktivieren  
 Sie können angeben, ob das Ausgabefenster in Ihrer Anwendung zu deaktivieren, durch Ändern des Werts der Zeile "DisableOutputWindow" in der *SolutionName*. Application.PKGDEF-Datei. Um das Fenster "Ausgabe" zu deaktivieren, legen Sie den Wert `dword:00000001`, und um das Fenster "Ausgabe" anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Ob im Hauptfenster von abgelegte Dateien zulassen  
 Sie können angeben, ob abgelegte Dateien im Hauptfenster der Anwendung zu ermöglichen, durch Ändern des Werts der Zeile "AllowsDroppedFilesOnMainWindow" in der *SolutionName*. Application.PKGDEF-Datei. Um abgelegten Dateien zu ermöglichen, legen Sie den Wert `dword:00000001`, und um die gelöschte Dateien nicht zulassen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Der Standard-Suchseite  
 Sie können anpassen, dass die Webseite für die Browser, welche Seite, die angezeigt wird, wird durch Ändern des Werts der Zeile "DefaultSearchPage" im Webbrowserfenster geöffnet, die *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-home-page"></a>Standard-Startseite  
 Sie können auf der Startseite anpassen, indem Sie die Änderung des Werts der Zeile "DefaultHomePage" in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierten Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Ob das Konzept der Lösung ausblenden  
 Sie können angeben, ob die Projektmappe in der Anwendung ausblenden durch Ändern des Werts der Zeile "HideSolutionConcept" in der *SolutionName*. Application.PKGDEF-Datei. Um die Projektmappe auszublenden, legen Sie den Wert `dword:00000001`, und um die Projektmappe anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Der Standard-Debugging-Modul  
 Sie können die Debugging-Modul, das Ihre Anwendung verwendet wird, durch Ändern des Werts der Zeile "DefaultDebugEngine" im Ändern der *SolutionName*. Application.PKGDEF-Datei, die die GUID des Debugging-Modul.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Die Dateierweiterung der Benutzerdatei Optionen  
 Sie können den Namen des Ordners die Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der Zeile "UserOptsFileExt" in ändern *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-solution-file-extension"></a>Die Dateierweiterung der Projektmappe  
 Sie können ändern, dass die Erweiterung für die Projektmappendateien durch Ändern des Werts der Zeile "SolutionFileExt" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-user-files-folder-root"></a>Der standardmäßige Benutzer Dateien Ordner Stamm  
 Sie können den Namen des Stammordners Benutzer Dateien für Ihre Anwendung ändern, durch Ändern des Werts der Zeile "UserFilesSubFolderName" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-solution-file-creator-identifier"></a>Die Lösung Ersteller Dateibezeichner  
 Sie können ändern, dass den Bezeichner für die Projektmappendateien verwendet wird, durch Ändern des Werts der Zeile "SolutionFileCreatorIdentifier" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-projects-location"></a>Der Standardspeicherort für Projekte  
 Sie können den Namen der Standardspeicherort für Projekte ändern, durch Ändern des Werts der Zeile "DefaultProjectsLocation" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-application-localization-package"></a>Das Anwendungspaket für die Lokalisierung  
 Sie können ändern, die Lokalisierung-Paket für Ihre Anwendung verwendet wird, durch Ändern des Werts der Zeile "AppLocalizationPackage" in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Ob den Stamm der Hierarchie im Titel anzeigen  
 Sie können angeben, ob den Stamm der Hierarchie in der Titelleiste in Ihrer Anwendung anzeigen, durch Ändern des Werts der Zeile "ShowHierarchyRootInTitle" in der *SolutionName*. Application.PKGDEF-Datei. Um den Stamm der Hierarchie anzuzeigen, legen Sie den Wert `dword:00000001`, und um den Stamm der Hierarchie auszublenden, legen Sie den Wert `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Angeben einer Startseite  
 Zum Angeben einer Startseite für die benutzerdefinierte Anwendung in der *SolutionName*. Application.PKGDEF-Datei, legen Sie als Wert für "DisableStartPage" `dword:00000000`, und wählen Sie unter `[$RootKey$\StartPage\Default]` den URI zum Speicherort der XAML-Datei festlegen:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 In der Datei Applicationcommands.vsct in die *SolutionName*UI-Projekt, kommentieren Sie den Eintrag "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Sie müssen hinzufügen, der XAML-Datei, und alle Graphics-Dateien, die Sie benötigen, zu der *SolutionName* Projekt. Diese Dateien müssen tatsächlich kopiert werden, um die *SolutionName* Projektverzeichnis ein, nicht von einem anderen Verzeichnis hinzugefügt.  
  
 Legen Sie für alle Dateien, die **Work Item Type** Eigenschaft, um **isolierten Shell-Datei** in der Reihenfolge für die Dateien zum Kopieren der *$RootFolder$* Verzeichnis. (Festlegen der **Work Item Type** -Eigenschaft, mit der rechten Maustaste in der das, und wählen Sie **Eigenschaften**. Diese Eigenschaft finden Sie unter **Konfigurationseigenschaften**, **allgemeine**.)  
  
 Weitere Informationen zum Anpassen von Startseiten finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Mithilfe von anderen Elementen der isolierte shell  
 Sie können andere Dateien und Projekte, die in der isolierten Shell-Projektmappenvorlage weiter anpassen, die Anwendung enthalten sind.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Aktivieren/Deaktivieren von Visual Studio-Pakete  
 Die *SolutionName*.pkgundef-Datei können Sie bestimmte Arten von Visual Studio-Funktion zu deaktivieren, indem Sie bestimmte Pakete ausschließen. Z. B. die folgende Zeile:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Entfernt das Projekt verschiedene Dateien aus dem Satz von Vorlagen für Projekte angezeigt, der **neues Projekt** Dialogfeld. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Aktivieren/Deaktivieren von Menübefehlen  
 Die *SolutionName*UI.vsct-Datei enthält eine Liste auskommentierten alle Menübefehle für isolierte Shell verfügbar. Um einen bestimmten Befehl zu deaktivieren, kommentieren Sie die entsprechende Zeile aus. Beispielsweise um die Teilung/Kommentar zu deaktivieren, heben Sie die auskommentierung der `<Define name="No_SplitCommand"/>` Zeile. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Das Bitmuster, das verwendet wird, auf dem Begrüßungsbildschirm  
 Sie können anpassen, dass das Bitmuster auf dem Begrüßungsbildschirm, also Fenster, das angezeigt wird, wenn die Anwendung gestartet wird, durch Ändern des Werts der Zeile in "SplashScreenBitmap", verwendet der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Die Hilfe/Informationen zu Fenstern  
 In der Vorlage isolierte Shell besteht ein separates Projekt Sie die Hilfe anpassen können/Informationsfeld für Ihre Anwendung. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).