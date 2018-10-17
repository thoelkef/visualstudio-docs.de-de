---
title: Bereitstellen von benutzerdefinierten Startseiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99520828ff4a6ac44ca4512b2104cb3019a9785a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235377"
---
# <a name="deploying-custom-start-pages"></a>Bereitstellen von benutzerdefinierten Startseiten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können benutzerdefinierte Startseiten mithilfe von VSIX-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mithilfe der Start-Seite-Projektvorlage  
 Wenn Sie eine Startseite mithilfe der Projektvorlage für die Startseite erstellen, und erstellen Sie das Projekt, erstellt Visual Studio eine VSIX-Datei, die Sie verteilen können. Eine Startseite in einer VSIX-Datei packen, können Sie die folgenden Optionen für die Bereitstellung abhängig von Ihrer Zielgruppe:  
  
-   Sie können die VSIX-Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website einfügen. Wenn eine Person die Datei geöffnet wird, wird die Startseite wird automatisch installiert.  
  
-   Sie können die VSIX-Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website aus, damit Benutzer sie mithilfe von installieren können **Erweiterungs-Manager**.  
  
 Die Startseite-Projektvorlage erstellt eine Kopie der standardmäßigen Visual Studio-Startseite, damit Sie die Kopie zu ändern und das Original beibehalten können.  
  
 Sie erhalten die Projektvorlage für die Startseite mit **Erweiterungs-Manager** oder indem Sie sie auf der Website herunterladen.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Start-Seite-Projektvorlage  
 Eine erfolgreiche VSIX-Bereitstellung erfordert eine Erweiterung in Ordnern installiert werden, die von der während der VSIX-Registrierung und erkannt werden **Erweiterungs-Manager**. Da die Projektvorlage der Startseite bereits die richtigen Ordnern angegeben wird, empfehlen wir, dass Sie es verwenden, um eine Erweiterung für VSIX-Bereitstellung zu verpacken. Wenn Sie einen Fall haben, in dem Sie die Vorlage verwenden können, können Sie jedoch eine VSIX-Bereitstellung erstellen, ohne die Verwendung.  
  
 Um eine VSIX-Bereitstellung ohne Verwendung der Projektvorlage für die Startseite zu erstellen, erstellen Sie zuerst eine VSIX-Datei für die Startseite in einem der beiden folgenden Weisen:  
  
-   Durch Hinzufügen Ihrer benutzerdefinierten Startseitendateien leeren VSIX-Projekt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
-   Durch das manuelle Erstellen einer VSIX-Datei. Weitere Informationen finden Sie unter [Vorgehensweise: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Für Visual Studio, eine Startseite zu erkennen die `Content Element` das VSIX-Manifest muss Sie enthalten eine `CustomExtension Element` , bei dem die `Type` -Attributsatz auf `"StartPage"`. Eine Erweiterung der Startseite, die installiert wurde, indem Sie mit der VSIX-Bereitstellung wird angezeigt, der **Customize Start Page** auf in der Liste der **Start** Optionen-Seite als **[installierte Extension]** *Erweiterungsnamen*.  
  
 Wenn Ihr Paket Startseite Assemblys enthält, müssen Sie Bindung Pfad Registrierung hinzufügen, damit sie beim Start von Visual Studio verfügbar sind. Zu diesem Zweck sicher, dass Ihr Paket eine PKGDEF-Datei enthält, die die folgenden Informationen enthält.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer  
 Installieren Erweiterungen, die in VSIX-Paketen bereitgestellt werden. standardmäßig nur für den aktuellen Benutzer. Sie können eine Installation der Startseite für alle Benutzer des Zielcomputers vornehmen, durch das Erstellen einer Bereitstellung für alle Benutzer.  
  
##### <a name="to-create-an-all-users-deployment"></a>Zum Erstellen einer Bereitstellung für alle Benutzer  
  
1.  Öffnen Sie die Datei "extension.vsixmanifest", in der Codeansicht.  
  
2.  In der `Identifier` -Element des Vsix-Manifests, Hinzufügen einer `AllUsers` -Element, das einem von Wert `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Dies bewirkt, dass das Vsix-Installationsprogramm, um für Administratorberechtigungen fordert, und installieren Sie die Dateien auf \Common7\IDE\Extensions.  
  
3.  Öffnen Sie die PKGDEF-Datei.  
  
4.  Ändern Sie die PKGDEF, um die Standardstartseite unter HKLM zu festlegen, indem Sie Folgendes ein, wobei *MyStartPage.xaml* ist der Name der XAML-Datei, die Startseite enthält.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Dadurch wird das Visual erstellt, in den neuen Speicherort für die Startseite zu suchen.  
  
## <a name="file-copy-deployment"></a>Datei-Copy-Bereitstellung  
 Sie müssen nicht zum Bereitstellen einer benutzerdefinierten Startseite eine VSIX-Datei zu erstellen. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den Ordner "\StartPages\" des Benutzers kopieren. Der **Customize Start Page** auf in der Liste der **Start** Seite "Optionen" listet alle XAML-Datei in diesem Ordner zusammen mit dem Pfad, z. B. %USERPROFILE%\My Documents\Visual Studio  *Version*\StartPages\\*Dateiname*XAML. Wenn Ihre Startseite Verweise auf private Assemblys enthält, müssen Sie kopieren und fügen Sie sie im Ordner "\PrivateAssemblies\".  
  
 Um eine Startseite zu verteilen, die Sie ohne Verpackung erstellt empfiehlt in einem VSIX-Datei, eine Strategie für die Basisdatei kopieren verwenden, z. B. ein Stapelverarbeitungsskript ausführen oder eine andere bereitstellungstechnologie, mit dem Sie legen Sie die Dateien in den Verzeichnissen erforderlichen.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie manuell eine benutzerdefinierte Startseite  
  
1.  Kopieren Sie die XAML-Datei, die im Markup der Seite starten, sowie alle unterstützenden Dateien als Assemblys enthält, und fügen Sie sie im Ordner "\StartPages\" des Benutzers.  
  
2.  Wenn Sie die Startseite erforderlich ist, kopieren Sie und fügen Sie sie in... \\ *Visual Studio-Installationsordner*\Common7\IDE\PrivateAssemblies\\.  
  
3.  In der **Customize Start Page** auf in der Liste der **Start** Optionen Seite, wählen Sie die neue Startseite. Weitere Informationen finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)

