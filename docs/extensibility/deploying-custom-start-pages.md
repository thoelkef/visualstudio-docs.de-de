---
title: Bereitstellen von benutzerdefinierten Startseiten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2217b77116ea561c32e96fcb7b92b520e680025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-custom-start-pages"></a>Bereitstellen von benutzerdefinierten Startseiten
Sie können benutzerdefinierte Startseiten mithilfe des VSIX-Bereitstellung oder durch Kopieren der Dateien auf die korrekten Speicherorte auf dem Zielcomputer bereitstellen.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mit der Start-Seite-Projektvorlage  
 Wenn Sie eine Startseite mithilfe der Projektvorlage für Startseiten erstellen, und erstellen Sie das Projekt, erstellt Visual Studio eine VSIX-Datei, die Sie verteilen können. Verpacken eine Startseite in einer VSIX-Datei bietet Ihnen die folgenden Optionen für die Bereitstellung, je nach Ihrer Zielgruppe:  
  
-   Sie können die VSIX-Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website einfügen. Wenn ein Benutzer die Datei geöffnet wird, wird die Startseite automatisch installiert.  
  
-   Sie können die VSIX-Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website, sodass Benutzern mithilfe von installiert werden kann **Erweiterungs-Manager**.  
  
 Die Projektvorlage für Startseiten erstellt eine Kopie der Standardkonfigurationsdatei Visual Studio-Startseite, damit Sie die Kopie zu ändern und die ursprünglichen beibehalten können.  
  
 Sie können mit der Projektvorlage für Startseiten abrufen **Erweiterungs-Manager** oder indem Sie ihn von der Website herunterladen.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Start-Seite-Projektvorlage  
 Eine erfolgreiche VSIX-Bereitstellung erfordert eine Erweiterung in Ordnern installiert werden, die von der VSIX-Registrierungsprozess und erkannt werden **Erweiterungs-Manager**. Da die Projektvorlage für Startseiten bereits die richtigen Ordnern angegeben wird, wird empfohlen, dass Sie ihn verwenden, wenn Sie eine Erweiterung für VSIX-Bereitstellung zu verpacken möchten. Wenn Sie einen Fall in dem Sie die Vorlage verwenden können, können Sie eine VSIX-Bereitstellung erstellen, ohne es.  
  
 Um eine VSIX-Bereitstellung erstellen, ohne die Projektvorlage für Startseiten verwenden, müssen Sie zunächst erstellen Sie eine VSIX-Datei für die Startseite in einem der beiden folgenden Weisen:  
  
-   Durch die benutzerdefinierte Startseite-Dateien werden ein leeres VSIX-Projekt hinzugefügt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
-   Erstellen Sie manuell eine VSIX-Datei. So erstellen Sie eine VSIX-Datei manuell  
    
    1.  Erstellen Sie die Datei "Extension.vsixmanifest" und der [Content_Types] .xml-Datei in einen neuen Ordner ein. Weitere Informationen finden Sie unter [Aufbau eines VSIX-Pakets](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
    2.  In Windows-Explorer mit der rechten Maustaste in des Ordners, der die zwei XML-Dateien enthält, klicken Sie auf Senden an und klicken Sie dann auf komprimierten (gezippten) Ordner. Benennen Sie die resultierende ZIP-Datei in Filename.vsix, wobei Dateiname den Namen der verteilbaren Datei ist, die das Paket installiert wird.  
  
 Für Visual Studio erkennt eine Startseite der `Content Element` des VSIX-Manifest muss enthalten eine `CustomExtension Element` , besitzt die `Type` -Attributsatz zur `"StartPage"`. Eine Startseite-Erweiterung, die mithilfe des VSIX-Bereitstellung installiert wurde angezeigt wird, der **Startseite anpassen** auf in der Liste der **Start** (Seite) als **[installierte Erweiterung]** *Erweiterungsnamen*.  
  
 Wenn Ihre Startseite Paket Assemblys enthält, müssen Sie Bindung Pfad Registrierung hinzufügen, damit sie beim Start von Visual Studio verfügbar sind. Zu diesem Zweck sicher, dass das Paket eine PKGDEF-Datei enthält, die die folgenden Informationen verfügt.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer  
 Installieren Erweiterungen im VSIX-Pakete bereitgestellt werden standardmäßig nur für den aktuellen Benutzer. Sie können bei der Installation eines Startseite für alle Benutzer des Zielcomputers vornehmen, durch das Erstellen einer Bereitstellung für alle Benutzer.  
  
##### <a name="to-create-an-all-users-deployment"></a>Zum Erstellen einer Bereitstellung für alle Benutzer  
  
1.  Öffnen Sie die Datei "Extension.vsixmanifest", in der Codeansicht.  
  
2.  In der `Identifier` Element des Vsix-Manifests hinzufügen, eine `AllUsers` Element, dessen Wert der `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Dies bewirkt, dass das VSIX-Installationsprogramm zur Administratorberechtigungen auffordert und befestigen Sie die Dateien an \Common7\IDE\Extensions.  
  
3.  Öffnen Sie die PKGDEF-Datei.  
  
4.  Ändern Sie die PKGDEF, um die Standardstartseite unter HKLM festzulegen, indem Sie den folgenden Code, in dem *MyStartPage.xaml* ist der Name der XAML-Datei, die Ihre Startseite enthält.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Das weist Visual Schmalseite in die neue Startseite Position gesucht werden soll.  
  
## <a name="file-copy-deployment"></a>Bereitstellung Kopierens von Dateien  
 Sie müssen keine VSIX-Datei zum Bereitstellen einer benutzerdefinierten Startseite erstellen zu können. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den Ordner "\StartPages\" die Benutzers kopieren. Die **Startseite anpassen** auf in der Liste der **Start** Seite "Optionen" listet alle XAML-Datei in diesem Ordner, zusammen mit dem Pfad – z. B. %USERPROFILE%\My Dateien\Visual Studio  *Version*\StartPages\\*Dateiname*XAML. Wenn Ihre Startseite Verweise auf private Assemblys enthält, müssen Sie kopieren und fügen Sie sie im Ordner "\PrivateAssemblies\".  
  
 Um eine Startseite zu verteilen, die Sie ohne Verpackung erstellt empfohlen in eine VSIX-Datei, die Verwendung einer Strategie für die grundlegende Datei kopieren, z. B. ein Batchskript oder eine andere bereitstellungstechnologie, mit dem Sie müssen sich die Dateien in den Verzeichnissen erforderlichen.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie manuell eine benutzerdefinierte Startseite  
  
1.  Kopieren Sie die XAML-Datei, die das Markup Startseite sowie alle unterstützenden Dateien als Assemblys enthält, und fügen Sie sie im Ordner "\StartPages\" des Benutzers.  
  
2.  Wenn die Startseite Assemblys erforderlich ist, kopieren Sie und fügen Sie sie in... \\ *Visual Studio-Installationsordner*\Common7\IDE\PrivateAssemblies\\.  
  
3.  In der **Startseite anpassen** auf in der Liste der **Start** Optionen Seite, wählen Sie die neue Startseite. Weitere Informationen finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)