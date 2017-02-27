---
title: "Anpassen der isolierte Shells | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Shell, isolierten Modus"
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Anpassen der isolierte Shells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Visual Studio isolated Shell\-Anwendung durch verschiedene Aspekte der Visual Studio\-Benutzeroberfläche ändern und beschränken die Befehle und Funktionen in Ihrer speziellen Anwendung anpassen.  
  
## Mithilfe der Application.pkgdef\-Datei  
 Die isolierte Shell Vorlagenprojektmappe enthält eine *SolutionName*. Application.PKGDEF\-Datei, die Sie die folgenden Funktionen ändern kann:  
  
##### Der Titel der Anwendung  
 Sie können anpassen, dass der Titel der Anwendung, also den Namen, die in der Titelleiste der Anwendung angezeigt wird, ändern Sie den Wert der Zeile "AppName" in der *SolutionName*. Application.PKGDEF\-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Wenn Sie den Titel der Anwendung, um das Projekt anzuzeigen, die gegenwärtig nicht wünschen, ändern Sie den Wert der Zeile "ShowHierarchyRootInTitle" in der *SolutionName*. Application.PKGDEF Datei aus DWORD: 00000001 DWORD: 00000000.  
  
##### Das Symbol der Anwendung  
 Sie können das Anwendungssymbol anpassen, das das Symbol ist, das indem der Anwendungsname in der Titelleiste der Anwendung angezeigt wird. Kopieren Sie ein anderes Symbol auf das Symbol Verzeichnis. In **Projektmappen\-Explorer**, fügen Sie das Symbol, um den Ordner Ressourcendateien. Anschließend öffnen Sie die Datei VSShellStub.rc, und Ersetzen Sie den Wert der IDI\_STUBPROGRAM durch den Namen des neuen Symbols. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Das Befehlszeilen\-logo  
 Sie können anpassen, das Befehlszeilen\-Logo, handelt der Text, der angezeigt wird, wenn die Anwendung über die Befehlszeile gestartet wird, ändern Sie den Wert der Zeile "CommandLineLogo" in der *SolutionName*. Application.PKGDEF\-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### Der Name des Unterordners Benutzer Dateien  
 Sie können den Namen des Ordners für die Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der Zeile "UserFilesSubFolderName" in ändern *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Der Titel des Knotens in der Projektmappe im Dialogfeld Neues Projekt  
 Sie können den Titel für den Projektmappenknoten im Dialogfeld Neues Projekt anpassen, indem Sie ändern den Wert der Zeile "NewProjDlgSlnTreeNodeTitle" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Der Header der installierten Vorlagen im Dialogfeld Neues Projekt  
 Sie können den Header der installierten Vorlagen im Dialogfeld Neues Projekt ändern, durch Ändern der Zeile "NewProjDlgInstalledTemplatesHdr" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Ob verschiedene Dateien standardmäßig ausblenden  
 Sie können angeben, ob verschiedene Dateien standardmäßig ausblenden, indem Sie den Wert der Zeile "HideMiscellaneousFilesByDefault" in der *SolutionName*. Application.PKGDEF\-Datei. Um verschiedene Dateien auszublenden, legen Sie den Wert `dword:00000001`, und um die Dateien anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### Ob das Ausgabefenster deaktivieren  
 Sie können angeben, ob das Ausgabefenster in Ihrer Anwendung zu deaktivieren, indem Sie ändern den Wert der Zeile "DisableOutputWindow" in der *SolutionName*. Application.PKGDEF\-Datei. Um das Ausgabefenster zu deaktivieren, legen Sie den Wert `dword:00000001`, und um das Ausgabefenster anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### Ob abgelegte Dateien des Hauptfensters zulassen  
 Sie können angeben, ob abgelegte Dateien im Hauptfenster der Anwendung zu erlauben, indem Sie ändern den Wert der Zeile "AllowsDroppedFilesOnMainWindow" in der *SolutionName*. Application.PKGDEF\-Datei. Um gelöschte Dateien zu ermöglichen, legen Sie den Wert `dword:00000001`, und um gelöschte Dateien nicht zuzulassen, legen Sie den Wert `dword:00000000`.  
  
##### Standardsuchseite  
 Sie können anpassen, dass der Webbrowser eine Seite, die Seite angezeigt wird, wenn ein Webbrowserfenster geöffnet wird, den Wert der Zeile "DefaultSearchPage" ändern, die *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Standard\-Startseite  
 Sie können die Startseite anpassen, durch Ändern der Zeile "DefaultHomePage" in der *SolutionName*. Application.PKGDEF\-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### Ob das Lösungskonzept ausblenden  
 Sie können angeben, ob die Lösung in Ihrer Anwendung ausblenden, indem Sie den Wert der Zeile "HideSolutionConcept" in der *SolutionName*. Application.PKGDEF\-Datei. Um die Projektmappe auszublenden, legen Sie den Wert `dword:00000001`, und um die Lösung anzuzeigen, legen Sie den Wert `dword:00000000`.  
  
##### Die Standard\-Debugging\-Modul  
 Sie können ändern, das Debugging\-Modul, das Ihre Anwendung verwendet wird, ändern Sie den Wert der Zeile "DefaultDebugEngine" in der *SolutionName*. Application.PKGDEF\-Datei, die die GUID des Debugging\-Modul.  
  
##### Die Erweiterung der Datei mit den Benutzer  
 Sie können den Namen des Ordners für die Anwendung für Benutzerdateien verwaltet durch Ändern des Werts der Zeile "UserOptsFileExt" in ändern *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Erweiterung der Lösung  
 Sie können ändern, dass die Erweiterung für die Projektmappendateien durch Ändern des Werts der Zeile "SolutionFileExt" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Der standardmäßige Benutzer Dateien Ordner Stamm  
 Sie können den Namen des Stammordners der Benutzerdateien für Ihre Anwendung ändern, indem Sie ändern den Wert der Zeile "UserFilesSubFolderName" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Die Lösung Ersteller Dateibezeichner  
 Sie können den Bezeichner für die Projektmappendateien durch Ändern des Werts der Zeile "SolutionFileCreatorIdentifier" zum Ändern der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Der Standardspeicherort für Projekte  
 Sie können den Namen der Standardspeicherort für Projekte ändern, ändern Sie den Wert der Zeile "DefaultProjectsLocation" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Das Anwendungspaket für die Lokalisierung  
 Sie können ändern, dass das Localization\-Paket für Ihre Anwendung verwendet wird, ändern Sie den Wert der Zeile "AppLocalizationPackage" in der *SolutionName*. Application.PKGDEF\-Datei.  
  
##### Ob Sie den Stamm der Hierarchie im Titel anzeigen  
 Sie können angeben, ob Sie den Stamm der Hierarchie in der Titelleiste in Ihrer Anwendung anzeigen, indem Sie den Wert der Zeile "ShowHierarchyRootInTitle" in der *SolutionName*. Application.PKGDEF\-Datei. Wenn den Stamm der Hierarchie anzeigen möchten, legen Sie den Wert `dword:00000001`, und um den Stamm der Hierarchie auszublenden, legen Sie den Wert `dword:00000000`.  
  
##### Angeben einer Startseite  
 An eine Startseite für Ihre benutzerdefinierte Anwendung, in der *SolutionName*. Application.PKGDEF\-Datei, legen Sie den Wert "DisableStartPage" `dword:00000000`, und wählen Sie unter `[$RootKey$\StartPage\Default]` den URI zum Speicherort der XAML\-Datei festlegen:  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 In der Datei Applicationcommands.vsct in die *SolutionName*UI\-Projekt, kommentieren Sie den Eintrag "No\_ShellPkg\_startPageCommand":  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Sie müssen hinzufügen, die XAML\-Datei und Grafikdateien, die Sie benötigen, zu der *SolutionName* Projekt. Diese Dateien müssen tatsächlich kopiert werden, um die *SolutionName* Projektverzeichnis, nicht von einem anderen Verzeichnis hinzugefügt.  
  
 Legen Sie alle Dateien, die **Elementtyp** \-Eigenschaft **isolierte Shell\-Datei** in der Reihenfolge für die Dateien zum Kopieren der *$RootFolder$* Verzeichnis. \(Festlegen der **Elementtyp** \-Eigenschaft, mit der rechten Maustaste in der das, und wählen Sie **Eigenschaften**. Diese Eigenschaft finden Sie unter **Konfigurationseigenschaften**, **Allgemeine**.\)  
  
 Weitere Informationen zum Anpassen von Startseiten finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## Mithilfe von anderen Elementen der isolierte shell  
 Sie können weitere Dateien und Projekte, die in der Projektmappenvorlage für isolierte Shell weiter anpassen, die Anwendung enthalten sind.  
  
##### Aktiviert bzw. deaktiviert die Visual Studio\-Pakete  
 Die *SolutionName*.pkgundef ermöglicht es Ihnen, bestimmte Arten von Visual Studio\-Funktion zu deaktivieren, indem Sie bestimmte Pakete ausschließen. Zum Beispiel die folgende Zeile:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Entfernt das Projekt verschiedene Dateien aus dem Satz von Vorlagen für Projekte angezeigt, der **Neues Projekt** Dialogfeld. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Aktiviert bzw. deaktiviert die Befehle im Menü  
 Die *SolutionName*UI.vsct\-Datei enthält eine auskommentierte Liste alle Befehle des Menüs für die isolierte Shell zur Verfügung. Um einen bestimmten Befehl zu deaktivieren, kommentieren Sie die entsprechende Zeile aus. Um die Teilung\/Kommentar zu deaktivieren, kommentieren Sie z. B. die `<Define name="No_SplitCommand"/>` Zeile. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Die Bitmap auf dem Begrüßungsbildschirm verwendet  
 Sie können anpassen, dass die Bitmap auf dem Begrüßungsbildschirm, der im Fenster angezeigt wird, wenn die Anwendung gestartet wird, den Wert der Zeile "SplashScreenBitmap" ändern, verwendet die *SolutionName*. Application.PKGDEF\-Datei. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### Die Hilfe\/Informationen über das Fenster  
 In der Vorlage isolierte Shell ist es ein separates Projekt Sie die Hilfe anpassen können\/Info\-Dialogfeld für die Anwendung. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer grundlegenden isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).