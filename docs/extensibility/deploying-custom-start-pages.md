---
title: Bereitstellen von benutzerdefinierten Startseiten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: dcc184d6aedb3e15bfddd8396c54b351ef4d3288
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693008"
---
# <a name="deploy-custom-start-pages"></a>Bereitstellen von benutzerdefinierten Startseiten

Sie können benutzerdefinierte Startseiten mithilfe von VSIX-Bereitstellung oder durch Kopieren der Dateien an die richtigen Speicherorte auf dem Zielcomputer bereitstellen.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mithilfe der Projektvorlage der Startseite

Wenn Sie eine Startseite mithilfe der Projektvorlage für die Startseite erstellen und anschließend das Projekt erstellen, erstellt Visual Studio eine *VSIX* -Datei, die Sie verteilen können. Verpacken eine Startseite in einem *VSIX* Datei bietet Ihnen die folgenden Optionen für die Bereitstellung abhängig von Ihrer Zielgruppe:

-   Sie können Einfügen der *VSIX* Datei auf einer Netzwerkfreigabe oder auf einer öffentlichen Website. Wenn eine Person die Datei geöffnet wird, wird die Startseite wird automatisch installiert.

-   Können Sie hochladen, die *VSIX* -Datei in die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website aus, damit Benutzer sie mithilfe von installieren können **Erweiterungs-Manager**.

Die Startseite-Projektvorlage erstellt eine Kopie der standardmäßigen Visual Studio-Startseite, damit Sie die Kopie zu ändern und das Original beibehalten können.

Sie erhalten die Projektvorlage für die Startseite mit **Erweiterungs-Manager** oder indem Sie sie auf der Website herunterladen.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Projektvorlage der Startseite
 Eine erfolgreiche VSIX-Bereitstellung erfordert eine Erweiterung in Ordnern installiert werden, die von der während der VSIX-Registrierung und erkannt werden **Erweiterungs-Manager**. Da die Projektvorlage der Startseite bereits die richtigen Ordnern angegeben wird, empfehlen wir, dass Sie es verwenden, um eine Erweiterung für VSIX-Bereitstellung zu verpacken. Wenn Sie einen Fall haben, in dem Sie die Vorlage verwenden können, können Sie jedoch eine VSIX-Bereitstellung erstellen, ohne die Verwendung.

 Um eine VSIX-Bereitstellung ohne Verwendung der Projektvorlage für die Startseite zu erstellen, erstellen Sie zunächst eine *VSIX* -Datei für die Startseite in einem der beiden folgenden Weisen:

- Durch Hinzufügen Ihrer benutzerdefinierten Startseitendateien leeren VSIX-Projekt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

- Durch das manuelle Erstellen einer *VSIX* Datei. Zum Erstellen einer *VSIX* Datei manuell:

   1. Erstellen der *"Extension.vsixmanifest"* Datei und die *[Content_Types] .xml* -Datei in einen neuen Ordner. Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

   2. Im Windows-Explorer den Ordner, die zwei XML-Dateien enthält, klicken Sie auf **senden an**, und klicken Sie dann auf komprimierten (gezippten) Ordner. Benennen Sie die resultierende *ZIP* Datei *Filename.vsix*, wobei der Dateiname der Name der verteilbaren Datei ist, die das Paket installiert wird.

Für Visual Studio, eine Startseite zu erkennen die `Content Element` das VSIX-Manifest muss Sie enthalten eine `CustomExtension Element` , bei dem die `Type` -Attributsatz auf `"StartPage"`. Eine Erweiterung der Startseite, die installiert wurde, indem Sie mit der VSIX-Bereitstellung wird angezeigt, der **Customize Start Page** auf in der Liste der **Start** Optionen-Seite als **[installierte Extension]** *Erweiterungsnamen*.

Wenn Ihr Paket Startseite Assemblys enthält, müssen Sie Bindung Pfad Registrierung hinzufügen, damit sie beim Start von Visual Studio verfügbar sind. Zu diesem Zweck stellen Sie sicher, dass das Paket enthält eine *PKGDEF* -Datei, die die folgenden Informationen enthält.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer
 Installieren Erweiterungen, die in VSIX-Paketen bereitgestellt werden. standardmäßig nur für den aktuellen Benutzer. Sie können eine Installation der Startseite für alle Benutzer des Zielcomputers vornehmen, durch das Erstellen einer Bereitstellung für alle Benutzer.

### <a name="to-create-an-all-users-deployment"></a>Zum Erstellen einer Bereitstellung für alle Benutzer

1.  Öffnen der *"Extension.vsixmanifest"* Datei in der Codeansicht.

2.  In der `Identifier` -Element des Vsix-Manifests, Hinzufügen einer `AllUsers` -Element, das einem von Wert `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Dies bewirkt, dass das Vsix-Installationsprogramm Administratorberechtigungen anfordern und installieren Sie dann auf die Dateien in *\Common7\IDE\Extensions*.

3.  Öffnen der *PKGDEF* Datei.

4.  Ändern der *PKGDEF* die Standardstartseite unter HKLM festlegen, durch das Hinzufügen der folgenden, in denen *MyStartPage.xaml* ist der Name des der *XAML* Datei starten mit Seite ".

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Dies teilt Visual Studio, in den neuen Speicherort für die Startseite zu suchen.

## <a name="file-copy-deployment"></a>Datei-Copy-Bereitstellung
 Sie müssen keine erstellen Sie eine *VSIX* Datei zum Bereitstellen einer benutzerdefinierten Startseite. Sie können stattdessen kopieren, das Markup und die unterstützenden Dateien direkt in des Benutzers <em>\StartPages\* Ordner. Die **Startseite anpassen</em>*  auf in der Liste der **Start** Optionen-Seite enthält alle *XAML* Dateien in diesem Ordner, zusammen mit dem Pfad – z. B. *%USERPROFILE%\My Documents\Visual Studio {Version} \StartPages\\{Dateiname} XAML*. Wenn Ihre Startseite Verweise auf private Assemblys enthält, müssen Sie das Kopieren und fügen Sie sie in der * \PrivateAssemblies\* Ordner.

 Startseite zu verteilen, die Sie erstellt haben, ohne das Verpacken in eine *VSIX* -Datei, es wird empfohlen, die Sie verwenden eine Basisdatei-kopieren-Strategie, z. B. ein Stapelverarbeitungsskript, oder legen Sie die Dateien einer anderen bereitstellungstechnologie, mit dem Sie die Erforderliche Verzeichnisse.

### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie manuell eine benutzerdefinierte Startseite

1.  Kopieren der *XAML* -Datei, die das Markup enthält, Startseite, sowie alle unterstützenden Dateien als Assemblys, und fügen sie des Benutzers * \StartPages\* Ordner.

2.  Wenn Sie die Startseite erforderlich ist, kopieren und fügen Sie sie in *... \\{Visual Studio-Installationsordner} \Common7\IDE\PrivateAssemblies\\*.

3.  In der **Customize Start Page** auf in der Liste der **Start** Optionen Seite, wählen Sie die neue Startseite. Weitere Informationen finden Sie unter [Startseite anpassen](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Siehe auch

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [Die Startseite Benutzersteuerelement hinzufügen](../extensibility/adding-user-control-to-the-start-page.md)