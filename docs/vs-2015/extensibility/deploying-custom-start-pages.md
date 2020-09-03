---
title: Bereitstellen von benutzerdefinierten Start Seiten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1cdd172c2960024da8b12735764161d36498c4e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162104"
---
# <a name="deploying-custom-start-pages"></a>Bereitstellen von benutzerdefinierten Startseiten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können benutzerdefinierte Start Seiten mithilfe der VSIX-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mithilfe der Projektvorlage für Start Seiten  
 Wenn Sie eine Startseite mithilfe der Projektvorlage für Startseiten erstellen und dann das Projekt erstellen, erstellt Visual Studio eine VSIX-Datei, die Sie verteilen können. Wenn Sie eine Start Seite in einer vsix-Datei packen, stehen Ihnen je nach Zielgruppe die folgenden Optionen für die Bereitstellung zur Verfügung:  
  
- Sie können die vsix-Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website ablegen. Wenn jemand die Datei öffnet, wird die Start Seite automatisch installiert.  
  
- Sie können die vsix-Datei auf die [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website hochladen, damit Benutzer Sie mithilfe des Erweiterungs- **Managers**installieren können.  
  
  Die Projektvorlage für Start Seiten erstellt eine Kopie der standardmäßigen Visual Studio-Startseite, sodass Sie die Kopie ändern und die ursprüngliche beibehalten können.  
  
  Sie können die Projektvorlage für Start Seiten mit dem **Erweiterungs-Manager** abrufen oder von der Website herunterladen.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Projektvorlage für Start Seiten  
 Eine erfolgreiche VSIX-Bereitstellung erfordert die Installation einer Erweiterung in Ordnern, die vom VSIX-Registrierungsprozess und vom **Erweiterungs-Manager**erkannt werden. Da die Projektvorlage für die Start Seite bereits die richtigen Ordner angibt, empfiehlt es sich, Sie immer dann zu verwenden, wenn Sie eine Erweiterung für die VSIX-Bereitstellung verpacken möchten. Wenn Sie jedoch einen Fall haben, in dem Sie die Vorlage nicht verwenden können, können Sie eine VSIX-Bereitstellung erstellen, ohne Sie zu verwenden.  
  
 Wenn Sie eine VSIX-Bereitstellung ohne die Startseiten-Projektvorlage erstellen möchten, erstellen Sie zunächst eine VSIX-Datei für die Startseite auf eine der beiden folgenden Weisen:  
  
- Durch Hinzufügen von benutzerdefinierten Start Seiten Dateien zu einem leeren VSIX-Projekt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
- Durch manuelles Erstellen einer vsix-Datei. Weitere Informationen finden Sie unter Vorgehens [Weise: Manuelles Verpacken einer Erweiterung (VSIX-Bereitstellung)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Damit Visual Studio eine Start Seite erkennt, muss der `Content Element` des VSIX-Manifests einen enthalten, bei `CustomExtension Element` dem das- `Type` Attribut auf festgelegt ist `"StartPage"` . Eine Startseiten Erweiterung, die mithilfe der VSIX-Bereitstellung installiert wurde, wird in der Liste **Startseite anpassen** auf der Seite **Start** Optionen als **[installierte Erweiterung]** *Erweiterungsname*angezeigt.  
  
  Wenn das Start Seiten Paket Assemblys enthält, müssen Sie die Bindungs Pfad Registrierung hinzufügen, damit diese beim Start von Visual Studio verfügbar sind. Stellen Sie zu diesem Zweck sicher, dass das Paket eine pkgdef-Datei mit den folgenden Informationen enthält.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer  
 Erweiterungen, die in VSIX-Paketen bereitgestellt werden, werden standardmäßig nur für den aktuellen Benutzer installiert. Sie können eine Start Seite für alle Benutzer des Ziel Computers installieren, indem Sie eine Bereitstellung für alle Benutzer erstellen.  
  
##### <a name="to-create-an-all-users-deployment"></a>So erstellen Sie eine Bereitstellung für alle Benutzer  
  
1. Öffnen Sie die Datei "Extension. vsixmanifest" in der Code Ansicht.  
  
2. `Identifier`Fügen Sie im-Element des VSIX-Manifests ein `AllUsers` Element mit dem Wert hinzu `true` .  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Dies bewirkt, dass der VSIX-Installer Administrator Berechtigungen auffordert und die Dateien dann in "\common7\ide\Extensions" installiert.  
  
3. Öffnen Sie die pkgdef-Datei.  
  
4. Ändern Sie die pkgdef-Datei, um die Standard Startseite unter HKLM festzulegen, indem Sie Folgendes hinzufügen, wobei *mystartpage. XAML* der Name der XAML-Datei ist, die Ihre Startseite enthält.  
  
     [$RootKey $ \startpage\standard]  
  
     "URI" = "$PackageFolder $ \\ *mystartpage. XAML*"  
  
     Dadurch wird die Visualisierung angezeigt, um am neuen Speicherort der Start Seite zu suchen.  
  
## <a name="file-copy-deployment"></a>Datei Kopier Bereitstellung  
 Zum Bereitstellen einer benutzerdefinierten Start Seite müssen Sie keine vsix-Datei erstellen. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den Ordner "\startpges\" des Benutzers kopieren. In der Liste **Startseite anpassen** auf der Seite **Start** Optionen werden alle XAML-Dateien in diesem Ordner und der Pfad aufgeführt – beispielsweise%USERPROFILE%\My Documents\Visual Studio *Version*\StartPages \\ *Dateiname*. XAML. Wenn die Start Seite Verweise auf private Assemblys enthält, müssen Sie Sie kopieren und in den Ordner \privateassemblies\ einfügen.  
  
 Zum Verteilen einer Start Seite, die Sie erstellt haben, ohne Sie in einer vsix-Datei zu packen, empfiehlt es sich, eine grundlegende Datei Kopier Strategie zu verwenden, z. b. ein Batch Skript oder eine beliebige andere Bereitstellungs Technologie, mit der Sie die Dateien in die erforderlichen Verzeichnisse einfügen können.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie eine benutzerdefinierte Start Seite manuell  
  
1. Kopieren Sie die XAML-Datei, die das Markup der Start Seite enthält, sowie alle unterstützenden Dateien, die keine Assemblys sind, und fügen Sie Sie in den Ordner "\startpages\" des Benutzers ein.  
  
2. Wenn die Start Seite Assemblys erfordert, kopieren Sie Sie, und fügen Sie Sie in ein. \\ *Visual Studio-Installationsordner*\common7\ide\privateassemblys \\ .  
  
3. Wählen Sie in der Liste **Startseite anpassen** auf der Seite **Start** Optionen die neue Startseite aus. Weitere Informationen finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen der Start Seite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
