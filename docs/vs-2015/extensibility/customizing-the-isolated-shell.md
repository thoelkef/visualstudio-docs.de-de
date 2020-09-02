---
title: Anpassen der isolierten Shell | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555967"
---
# <a name="customizing-the-isolated-shell"></a>Anpassen der isolierten Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihre Visual Studio-Anwendung für isolierte Shell anpassen, indem Sie verschiedene Aspekte der Visual Studio-Benutzeroberfläche ändern und die Befehle und Funktionen in ihrer spezialisierten Anwendung einschränken.  
  
## <a name="using-the-applicationpkgdef-file"></a>Verwenden der Datei "Application. pkgdef"  
 Die Lösung für isolierte shellvorlagen enthält einen *SolutionName*. Datei "Application. pkgdef", die es Ihnen ermöglicht, die folgenden Funktionen zu ändern:  
  
##### <a name="the-application-title"></a>Anwendungs Titel  
 Sie können den Anwendungs Titel anpassen, d. h. den Namen, der in der Titelleiste der Anwendung angezeigt wird, indem Sie den Wert der Zeile "appname" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Wenn der Anwendungs Titel das aktuell geladene Projekt nicht anzeigen soll, ändern Sie den Wert der Zeile "showhierarchyrootintitle" in " *SolutionName*". Application. pkgdef-Datei von DWORD: 00000001 to DWORD: 00000000.  
  
##### <a name="the-application-icon"></a>Anwendungssymbol  
 Sie können das Anwendungssymbol anpassen, bei dem es sich um das Symbol handelt, das durch den Anwendungsnamen in der Titelleiste der Anwendung angezeigt wird. Kopieren Sie ein anderes Symbol in das Symbol Verzeichnis. Fügen Sie in **Projektmappen-Explorer**das Symbol zum Ordner Ressourcen Dateien hinzu. Öffnen Sie dann die Datei vsshellstub. RC, und ersetzen Sie den Wert IDI_STUBPROGRAM durch den Namen des neuen Symbols. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Das Befehlszeilen Logo  
 Sie können das Befehlszeilen Logo anpassen, bei dem es sich um den Text handelt, der beim Starten der Anwendung über die Befehlszeile angezeigt wird, indem Sie den Wert der Zeile "commandlinelogo" in *SolutionName*ändern. Pkgdef-Datei der Anwendung. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md) .  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Der Name des unter Ordners der Benutzer Dateien.  
 Sie können den Namen des Ordners, der von der Anwendung für Benutzer Dateien verwaltet wird, ändern, indem Sie den Wert der Zeile "userfilessubfoldername" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Der Titel des projektmappenstrukturknotens im Dialogfeld "Neues Projekt"  
 Sie können den Titel des Projektmappenknotens im Dialogfeld "Neues Projekt" anpassen, indem Sie den Wert der Zeile "newprojdlgslntreenodetitle" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>Der Header "installierte Vorlagen" im Dialogfeld "Neues Projekt"  
 Sie können den Header "installierte Vorlagen" im Dialogfeld "Neues Projekt" ändern, indem Sie den Wert der Zeile "newprojdlginstalledtemplateshdr" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Gibt an, ob verschiedene Dateien standardmäßig ausgeblendet werden sollen.  
 Sie können angeben, ob verschiedene Dateien standardmäßig ausgeblendet werden sollen, indem Sie den Wert der Zeile "hidemiscellaneousfilesbydefault" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Wenn Sie verschiedene Dateien ausblenden möchten, legen Sie den Wert fest `dword:00000001` , und legen Sie zum Anzeigen der Dateien den Wert fest `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Gibt an, ob das Ausgabefenster deaktiviert werden soll.  
 Sie können angeben, ob das Ausgabefenster in der Anwendung deaktiviert werden soll, indem Sie den Wert der Zeile "disableoutputwindow" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Legen Sie zum Deaktivieren des Ausgabe Fensters den Wert fest `dword:00000001` , und legen Sie zum Anzeigen des Ausgabe Fensters den Wert fest `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Gibt an, ob gelöschte Dateien im Hauptfenster zugelassen werden sollen.  
 Sie können angeben, ob gelöschte Dateien im Hauptfenster der Anwendung zugelassen werden sollen, indem Sie den Wert der Zeile "allowsdroppedfilesonmainwindow" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Um gelöschte Dateien zuzulassen, legen Sie den Wert fest `dword:00000001` , und legen Sie den Wert fest, um gelöschte Dateien nicht zuzulassen `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Die Standard Suchseite  
 Sie können die Webbrowser Seite anpassen, bei der es sich um eine Seite handelt, die beim Öffnen des Webbrowser Fensters angezeigt wird, indem Sie den Wert der Zeile "defaultsearchpage" in *SolutionName*ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-default-home-page"></a>Die Standard Startseite  
 Sie können die Startseite anpassen, indem Sie den Wert der Zeile "DefaultHomePage" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md) .  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Gibt an, ob das Lösungskonzept ausgeblendet werden soll.  
 Sie können angeben, ob die Projekt Mappe in der Anwendung ausgeblendet werden soll, indem Sie den Wert der Zeile "hidesolutionconcept" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Um die Projekt Mappe auszublenden, legen Sie den Wert fest `dword:00000001` , und legen Sie zum Anzeigen der Projekt Mappe den Wert fest `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Die Standard-Debug-Engine  
 Sie können die von der Anwendung verwendete Debug-Engine ändern, indem Sie den Wert der Zeile "defaultdebugengine" in " *SolutionName*" ändern. Die Datei "Application. pkgdef" in die GUID der Debug-Engine.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Die Dateierweiterung der Benutzer Optionsdatei.  
 Sie können den Namen des Ordners, der von der Anwendung für Benutzer Dateien verwaltet wird, ändern, indem Sie den Wert der Zeile "useroptfileext" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-solution-file-extension"></a>Die Projektmappendatei-Erweiterung  
 Sie können die für die Projektmappendateien verwendete Erweiterung ändern, indem Sie den Wert der Zeile "solutionfileext" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-default-user-files-folder-root"></a>Der Standardordner für Benutzer Dateien  
 Sie können den Namen des Stamm Ordners der Benutzer Dateien für die Anwendung ändern, indem Sie den Wert der Zeile "userfilessubfoldername" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-solution-file-creator-identifier"></a>Der Bezeichner der Projektmappendatei  
 Sie können den Bezeichner für die Projektmappendateien ändern, indem Sie den Wert der Zeile "solutionfilekreatoridentifier" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-default-projects-location"></a>Der Standard Speicherort für Projekte  
 Sie können den Namen des Standard Projekt Speicher Orts ändern, indem Sie den Wert der Zeile "defaultprojectslocation" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="the-application-localization-package"></a>Das Anwendungslokalisierungs-Paket  
 Sie können das Lokalisierungs Paket ändern, das für Ihre Anwendung verwendet wird, indem Sie den Wert der Zeile "applocalizationpackage" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Gibt an, ob der Hierarchie Stamm im Titel angezeigt werden soll.  
 Sie können angeben, ob der Hierarchie Stamm in der Titelleiste der Anwendung angezeigt werden soll, indem Sie den Wert der Zeile "showhierarchyrootintitle" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Um den Hierarchie Stamm anzuzeigen, legen Sie den Wert fest `dword:00000001` , und legen Sie den Wert fest, um den Hierarchie Stamm auszublenden `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Angeben einer Startseite  
 Zum Angeben einer Startseite für die benutzerdefinierte Anwendung in *SolutionName*. Application. pkgdef-Datei, legen Sie den Wert "disablestartpage" auf fest `dword:00000000` , und unter `[$RootKey$\StartPage\Default]` legen Sie den URI auf den Speicherort der XAML-Datei fest:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Kommentieren Sie in der Datei "ApplicationCommands. vsct" im Projekt " *Projektmappenname*" den Eintrag "No_ShellPkg_startPageCommand" aus:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Sie müssen die XAML-Datei und alle benötigten Grafikdateien dem Projekt Projektmappenname *SolutionName* hinzufügen. Diese Dateien müssen tatsächlich in das Projektmappenverzeichnis " *Projektmappenname* " kopiert und nicht aus einem anderen Verzeichnis hinzugefügt werden.  
  
 Legen Sie für alle Dateien die Eigenschaft **Elementtyp** auf **isolierte Shelldatei** fest, damit die Dateien in das Verzeichnis *$RootFolder $* kopiert werden. (Um die Eigenschaft **Elementtyp** festzulegen, klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften**. Diese Eigenschaft finden Sie unter **Konfigurations Eigenschaften**, **Allgemein**.)  
  
 Weitere Informationen zum Anpassen von Startseiten finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Verwenden anderer Elemente der isolierten Shell  
 Sie können andere Dateien und Projekte verwenden, die in der Lösungs Vorlage für isolierte Shell enthalten sind, um die Anwendung weiter anzupassen.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Aktivieren/Deaktivieren von Visual Studio-Paketen  
 Die Datei " *SolutionName*. pkgundef" ermöglicht es Ihnen, bestimmte Arten von Visual Studio-Funktionen zu deaktivieren, indem bestimmte Pakete ausgeschlossen werden. Beispielsweise die folgende Zeile:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 entfernt das Projekt "sonstige Dateien" aus dem Satz von Projektvorlagen, die im Dialogfeld " **Neues Projekt** " angezeigt werden. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Menübefehle aktivieren/deaktivieren  
 Die Datei " *SolutionName*UI. vsct" enthält eine auskommentiertes Liste aller Menübefehle, die für die isolierte Shell verfügbar sind. Um einen bestimmten Befehl zu deaktivieren, heben Sie die Auskommentierung der entsprechenden Zeile auf. Um z. b. den Fenster-/geteiltekommentar zu deaktivieren, heben Sie die Auskommentierung der `<Define name="No_SplitCommand"/>` Zeile Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Die auf dem Begrüßungsbildschirm verwendete Bitmap.  
 Sie können die auf dem Begrüßungsbildschirm verwendete Bitmap anpassen, bei der es sich um das Fenster handelt, das beim Starten der Anwendung angezeigt wird, indem Sie den Wert der Zeile "splashscreenbitmap" in " *SolutionName*" ändern. Pkgdef-Datei der Anwendung. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Das Fenster "Hilfe/Informationen"  
 In der Vorlage für isolierte Shell gibt es ein separates Projekt, das Sie verwenden können, um das Feld "Hilfe/Info" für Ihre Anwendung anzupassen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
