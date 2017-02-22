---
title: "Bereitstellen von benutzerdefinierte Startseiten | Microsoft Docs"
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
  - "Paket-Startseite"
  - "Bereitstellen der Startseite"
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Bereitstellen von benutzerdefinierte Startseiten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können benutzerdefinierte Startseiten mithilfe des VSIX\-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.  
  
## VSIX\-Bereitstellung mit der Start\-Seite\-Projektvorlage  
 Wenn Sie eine Startseite mithilfe der Projektvorlage für die Startseite erstellen und anschließend das Projekt erstellen, erstellt Visual Studio eine VSIX\-Datei, die Sie verteilen können. Verpacken eine Startseite in einer VSIX\-Datei können Sie die folgenden Optionen für die Bereitstellung, je nach Ihrer Zielgruppe:  
  
-   Sie können die VSIX\-Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website einfügen. Wenn die Datei geöffnet wird, wird die Seite automatisch installiert.  
  
-   Sie können die VSIX\-Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) \-Website, damit Benutzer mit installieren können **Extension Manager**.  
  
 Die Startseite\-Projektvorlage erstellt eine Kopie der Visual Studio\-Startseite, damit Sie den ursprünglichen beibehalten und Kopie ändern können.  
  
 Sie können die Projektvorlage Startseite erhalten, indem **Extension Manager** oder von der Website heruntergeladen.  
  
## VSIX\-Bereitstellung ohne Verwendung der Start\-Projekt  
 Eine erfolgreiche VSIX\-Bereitstellung erfordert eine Erweiterung in Ordnern installiert werden, die von den VSIX\-Registrierungsvorgang und erkannt werden **Extension Manager**. Da die Projektvorlage Startseite bereits die richtigen Ordnern angegeben ist, wird empfohlen, dass Sie es verwenden, wenn Sie eine Erweiterung für das VSIX\-Bereitstellung zusammenfassen möchten. Wenn Sie einen Fall haben, in dem Sie die Vorlage verwenden können, können Sie eine VSIX\-Bereitstellung erstellen, ohne Sie.  
  
 Zum Erstellen einer VSIX\-Bereitstellung ohne Verwendung der Projektvorlage für die Startseite erstellen Sie zuerst eine VSIX\-Datei für die Startseite in einem der folgenden zwei Methoden:  
  
-   Durch benutzerdefinierte Startseite Dateien leeren VSIX\-Projekt hinzugefügt. Weitere Informationen finden Sie unter [VSIX\-Projektvorlage](../extensibility/vsix-project-template.md).  
  
-   Durch das manuelle Erstellen einer VSIX\-Datei. Weitere Informationen finden Sie unter [Gewusst wie: Manuelles Verpacken einer Erweiterung \(VSIX\-Bereitstellung\)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Für Visual Studio eine Seite starten, erkennt der `Content Element` das VSIX\-Manifest muss enthalten eine `CustomExtension Element` bei dem die `Type` \-Attributsatz zur `"StartPage"`. Eine Startseite\-Erweiterung, die installiert wurde, indem Sie mithilfe des VSIX\-Bereitstellung wird angezeigt, der **Startseite anpassen** auf in der Liste der **Start** Optionen\-Seite als **\[installierte Erweiterung\]** *Erweiterungsnamen*.  
  
 Wenn das Paket Startseite Assemblys enthält, müssen Sie Bindung Pfad Registrierung hinzufügen, damit diese beim Start von Visual Studio verfügbar sind. Zu diesem Zweck stellen Sie sicher, dass das Paket eine PKGDEF\-Datei enthält, die die folgende Informationen ein.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### VSIX\-Bereitstellung für alle Benutzer  
 Installieren Erweiterungen in VSIX\-Pakete bereitgestellt werden standardmäßig nur für den aktuellen Benutzer. Sie können eine Startseite Installation für alle Benutzer des Zielcomputers vornehmen, durch das Erstellen einer Bereitstellung für alle Benutzer.  
  
##### Erstellen eine Bereitstellung für alle Benutzer  
  
1.  Öffnen Sie die Datei "Extension.vsixmanifest", in der Codeansicht.  
  
2.  In der `Identifier` \-Element für das Vsix\-Manifest hinzufügen ein `AllUsers` \-Element, das den Wert `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Dies bewirkt, dass das Vsix\-Installationsprogramm Berechtigungen anfordern, und installieren Sie die Dateien auf \\Common7\\IDE\\Extensions.  
  
3.  Öffnen Sie die PKGDEF\-Datei.  
  
4.  Ändern Sie die PKGDEF die Standardstartseite unter HKLM zu festlegen, indem Sie Folgendes hinzufügen, in dem *MyStartPage.xaml* ist der Name der XAML\-Datei, die Ihre Startseite enthält.  
  
     \[$RootKey$ \\StartPage\\Default\]  
  
     "Uri"\="$PackageFolder$ \\*MyStartPage.xaml*"  
  
     Dies weist Visual bewährt, in den neuen Speicherort für die Startseite zu suchen.  
  
## Bereitstellung von Dateien kopieren  
 Sie müssen keinen erstellen Sie eine VSIX\-Datei, um eine benutzerdefinierte Startseite bereitzustellen. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den Ordner des Benutzers \\StartPages\\ kopieren. Die **Startseite anpassen** auf in der Liste der **Start** Seite listet alle XAML\-Datei in diesem Ordner zusammen mit dem Pfad – z. B. %USERPROFILE%\\My Documents\\Visual Studio *Version*\\StartPages\\*Dateinamen*XAML. Ihre Startseite Verweise auf private Assemblys enthält, müssen kopieren Sie sie und in den Ordner \\PrivateAssemblies\\ einfügen.  
  
 Um eine Startseite zu verteilen, die Sie ohne Verpackung erstellt empfohlen in eine VSIX\-Datei, die Verwendung einer Strategie für die grundlegende Datei kopieren, z. B. ein Batch\-Skript oder eine andere bereitstellungstechnologie, mit dem Sie legen Sie die Dateien in den Verzeichnissen erforderlichen.  
  
#### So installieren Sie manuell eine benutzerdefinierte Startseite  
  
1.  Kopieren Sie die XAML\-Datei, die das Markup Startseite sowie alle unterstützenden Dateien als Assemblys enthält, und fügen Sie sie in den Ordner des Benutzers \\StartPages\\.  
  
2.  Wenn die Seite erforderlich ist, kopieren und Einfügen in... \\*Visual Studio\-Installationsordner*\\Common7\\IDE\\PrivateAssemblies\\.  
  
3.  In der **Startseite anpassen** auf in der Liste der **Start** Optionen Seite, wählen Sie die neue Startseite. Weitere Informationen finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Hinzufügen des Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)