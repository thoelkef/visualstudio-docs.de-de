---
title: Anpassen der Isolated Shell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959899"
---
# <a name="customizing-the-isolated-shell"></a>Anpassen der Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihrem Visual Studio isolated Shell-Anwendung durch verschiedene Aspekte der Visual Studio-Benutzeroberfläche ändern und beschränken die Befehle und Funktionen in Ihrer speziellen Anwendung anpassen.  
  
## <a name="using-the-applicationpkgdef-file"></a>Mithilfe der Application.pkgdef-Datei  
 Die isolierte Shell-Vorlagenprojektmappe enthält eine *SolutionName*. Application.PKGDEF-Datei, die Ihnen ermöglicht, ändern Sie die folgenden Funktionen:  
  
##### <a name="the-application-title"></a>Den Anwendungstitel  
 Sie können anpassen, den Anwendungstitel, die den Namen, die in der Titelleiste der Anwendung angezeigt wird darstellt, durch Ändern des Werts der Zeile "AppName" in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Wenn Sie den Anwendungstitel auf das Projekt anzuzeigen, die derzeit geladen wird, nicht möchten, ändern Sie den Wert der Zeile "ShowHierarchyRootInTitle" in der *SolutionName*. Application.PKGDEF-Datei von DWORD: 00000001 auf DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Das Symbol der Anwendung  
 Sie können das Anwendungssymbol, anpassen, das Symbol, das von den Anwendungsnamen in der Titelleiste der Anwendung angezeigt wird. Kopieren Sie ein anderes Symbol in der Symbol-Verzeichnis. In **Projektmappen-Explorer**, das Symbol "Ordner" Ressourcen "hinzufügen". Klicken Sie dann öffnen Sie die VSShellStub.rc-Datei, und Ersetzen Sie den Wert der IDI_STUBPROGRAM durch den Namen des neuen Symbols. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Das Befehlszeilen-logo  
 Sie können anpassen, dass das Befehlszeile-Logo, d.h. dem Text, der angezeigt wird, wenn die Anwendung über die Befehlszeile gestartet wird, durch Ändern des Werts der "CommandLineLogo" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Der Name des Unterordners Benutzer Dateien  
 Sie können den Namen des Ordners, die Ihre Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der "UserFilesSubFolderName" in Zeile ändern *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Der Titel des Knotens in der Lösung in das Dialogfeld "Neues Projekt"  
 Sie können den Titel der Knoten "Projektmappe" in das Dialogfeld "Neues Projekt" anpassen, durch Ändern des Werts der "NewProjDlgSlnTreeNodeTitle" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Der installierten Vorlagen-Header in das Dialogfeld "Neues Projekt"  
 Sie können den installierten Vorlagen-Header in das Dialogfeld "Neues Projekt" ändern, durch Ändern des Werts der "NewProjDlgInstalledTemplatesHdr" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Ob Sie verschiedene Dateien standardmäßig ausblenden  
 Sie können angeben, ob verschiedene Dateien standardmäßig ausblenden, durch Ändern des Werts der "HideMiscellaneousFilesByDefault" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Um verschiedene Dateien auszublenden, legen Sie den Wert `dword:00000001`, und um die Dateien anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Ob das Fenster "Ausgabe" deaktivieren  
 Sie können angeben, ob das Fenster "Ausgabe" in Ihrer Anwendung zu deaktivieren, durch Ändern des Werts der "DisableOutputWindow" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Um das Fenster "Ausgabe" zu deaktivieren, legen Sie den Wert `dword:00000001`, und um das Fenster "Ausgabe" anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Ob abgelegte Dateien in das Hauptfenster zu ermöglichen  
 Sie können angeben, ob abgelegte Dateien in das Hauptfenster in Ihrer Anwendung zu ermöglichen, durch Ändern des Werts der "AllowsDroppedFilesOnMainWindow" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Um abgelegten Dateien zu ermöglichen, legen Sie den Wert `dword:00000001`, und um abgelegten Dateien nicht zuzulassen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>Die Standardseite für die Suche  
 Sie können anpassen, dass der Webbrowser eine Seite, die Seite, der angezeigt wird ist, wenn im Webbrowserfenster geöffnet wird, durch Ändern des Werts der "DefaultSearchPage" in Zeile, die *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-home-page"></a>Standard-Startseite  
 Sie können auf der Startseite anpassen, indem Sie die Änderung des Werts der "DefaultHomePage" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Ob das Lösungskonzept ausblenden  
 Sie können angeben, ob die Lösung in Ihrer Anwendung ausblenden, indem Sie die Änderung des Werts der "HideSolutionConcept" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Um die Projektmappe auszublenden, legen Sie den Wert `dword:00000001`, und um die Projektmappe anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Die Standard-Debug-engine  
 Sie können ändern, dass die Debug-Engine, die Ihre Anwendung verwendet wird, durch Ändern des Werts der "DefaultDebugEngine" Zeile in der *SolutionName*. Application.PKGDEF-Datei, die die GUID der Debug-Engine.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Die Dateierweiterung der Datei mit den Benutzer  
 Sie können den Namen des Ordners, die Ihre Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der "UserOptsFileExt" in Zeile ändern *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-solution-file-extension"></a>Die Dateierweiterung der Projektmappe  
 Sie können ändern, dass die Erweiterung für die Projektmappendateien verwendet werden, durch Ändern des Werts der "SolutionFileExt" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-user-files-folder-root"></a>Der standardmäßige Benutzer Dateien-Ordner Stamm.  
 Sie können den Namen des Stammordners der Benutzerdateien für Ihre Anwendung ändern, durch Ändern des Werts der "UserFilesSubFolderName" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-solution-file-creator-identifier"></a>Dateibezeichner Ersteller der Lösung  
 Sie können ändern, dass den Bezeichner für die Projektmappendateien durch Ändern des Werts der "SolutionFileCreatorIdentifier" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-default-projects-location"></a>Der Standardspeicherort für Projekte  
 Sie können den Namen der Standardspeicherort für Projekte ändern, durch Ändern des Werts der "DefaultProjectsLocation" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="the-application-localization-package"></a>Das Anwendungspaket für die Lokalisierung  
 Sie können ändern, der Localization-Paket für Ihre Anwendung verwendet wird, durch Ändern des Werts der "AppLocalizationPackage" Zeile in der *SolutionName*. Application.PKGDEF-Datei.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Ob Sie den Hierarchiestamm im Titel anzeigen  
 Sie können angeben, ob den Hierarchiestamm in der Titelleiste in Ihrer Anwendung angezeigt wird, durch Ändern des Werts der "ShowHierarchyRootInTitle" Zeile in der *SolutionName*. Application.PKGDEF-Datei. Um den Hierarchiestamm anzuzeigen, legen Sie den Wert `dword:00000001`, und um den Hierarchiestamm auszublenden, legen Sie den Wert `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Angeben einer Startseite  
 Angeben eine Startseite für Ihre benutzerdefinierte Anwendung in der *SolutionName*. Application.PKGDEF-Datei, legen Sie den Wert "DisableStartPage" `dword:00000000`, und wählen Sie unter `[$RootKey$\StartPage\Default]` legen Sie den URI an den Speicherort der XAML-Datei:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 In der Datei Applicationcommands.vsct in die *SolutionName*UI-Projekt, kommentieren Sie den Eintrag "No_ShellPkg_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Sie müssen hinzufügen, die XAML-Datei, und alle Graphics-Dateien, die Sie benötigen, zu der *SolutionName* Projekt. Diese Dateien müssen tatsächlich kopiert werden, um die *SolutionName* Projektverzeichnis nicht von einem anderen Verzeichnis hinzugefügt.  
  
 Für alle Dateien, Festlegen der **Elementtyp** Eigenschaft **isolierte Shell-Datei** in der Reihenfolge für die Dateien kopiert werden die *$RootFolder$* Verzeichnis. (Festlegen der **Elementtyp** -Eigenschaft, mit der rechten Maustaste in der das, und wählen Sie **Eigenschaften**. Diese Eigenschaft finden Sie unter **Konfigurationseigenschaften**, **allgemeine**.)  
  
 Weitere Informationen zum Anpassen der Startseiten, finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Verwenden andere Elemente der isolated shell  
 Sie können weitere Dateien und Projekte, die in der isolierten Shell-Projektmappenvorlage weiter anpassen, Ihre Anwendung enthalten sind.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Aktivieren/Deaktivieren von Visual Studio-Pakete  
 Die *SolutionName*pkgundef-Datei können Sie bestimmte Arten von Visual Studio-Funktionen zu deaktivieren, indem Sie bestimmte Pakete ausschließen. Z. B. die folgende Zeile:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Entfernt das Projekt verschiedene Dateien aus dem Satz von Projektvorlagen, die angezeigt wird, der **neues Projekt** Dialogfeld. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Aktivieren/Deaktivieren von Menübefehlen  
 Die *SolutionName*UI.vsct-Datei enthält eine Liste auskommentierte alle die Befehle im Menü der isolated Shell zur Verfügung. Um einen bestimmten Befehl zu deaktivieren, kommentieren Sie die entsprechende Zeile aus. Z. B. um den Kommentar Window Split/zu deaktivieren, heben Sie die auskommentierung der `<Define name="No_SplitCommand"/>` Zeile. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Die Bitmap, die auf dem Begrüßungsbildschirm verwendet  
 Sie können anpassen, dass die Bitmap, die auf dem Begrüßungsbildschirm, wird das Fenster, das angezeigt wird, wenn die Anwendung durch Ändern des Werts, der in Zeile "SplashScreenBitmap" gestartet wird, verwendet der *SolutionName*. Application.PKGDEF-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Die Hilfe/über Fenster  
 In der isolierten Shell-Vorlage besteht ein separates Projekt Sie anpassen, die Hilfe können/Info-Dialogfeld für Ihre Anwendung. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
