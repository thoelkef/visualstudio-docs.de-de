---
title: Bereitstellen benutzerdefinierter Startseiten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712226"
---
# <a name="deploy-custom-start-pages"></a>Bereitstellen benutzerdefinierter Startseiten

Sie können benutzerdefinierte Startseiten bereitstellen, indem Sie die VSIX-Bereitstellung verwenden oder die Dateien an die richtigen Speicherorte auf dem Zielcomputer kopieren.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>VSIX-Bereitstellung mithilfe der Projektvorlage "Startseite"

Wenn Sie eine Startseite mithilfe der Projektvorlage Startseite erstellen und dann das Projekt erstellen, erstellt Visual Studio eine *VSIX-Datei,* die Sie verteilen können. Das Verpacken einer Startseite in einer *vSix-Datei* bietet Ihnen je nach Zielgruppe die folgenden Optionen für die Bereitstellung:

- Sie können die *.vsix-Datei* auf einer Netzwerkfreigabe oder auf einer öffentlichen Website abspeichern. Wenn jemand die Datei öffnet, wird die Startseite automatisch installiert.

- Sie können die *.vsix-Datei* auf die [Visual Studio Marketplace-Website](https://marketplace.visualstudio.com/) hochladen, damit Benutzer sie mithilfe von **Extension Manager**installieren können.

Die Projektvorlage Startseite erstellt eine Kopie der standardmäßigen Visual Studio-Startseite, sodass Sie die Kopie ändern und das Original beibehalten können.

Sie können die Projektvorlage Startseite mithilfe des **Erweiterungs-Managers** oder durch Herunterladen von der Website abrufen.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX-Bereitstellung ohne Verwendung der Projektvorlage "Startseite"
 Eine erfolgreiche VSIX-Bereitstellung erfordert die Installation einer Erweiterung in Ordnern, die vom VSIX-Registrierungsprozess und von **Extension Manager**erkannt werden. Da die Projektvorlage Startseite bereits die richtigen Ordner angibt, wird empfohlen, sie immer dann zu verwenden, wenn Sie eine Erweiterung für die VSIX-Bereitstellung verpacken möchten. Wenn Sie jedoch einen Fall haben, in dem Sie die Vorlage nicht verwenden können, können Sie eine VSIX-Bereitstellung erstellen, ohne sie zu verwenden.

 Um eine VSIX-Bereitstellung ohne Verwendung der Projektvorlage Startseite zu erstellen, erstellen Sie zunächst eine *VSIX-Datei* für die Startseite auf eine der beiden folgenden Arten:

- Durch Hinzufügen Ihrer benutzerdefinierten Startseitendateien zu einem leeren VSIX-Projekt. Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

- Durch manuelles Erstellen einer *.vsix-Datei.* So erstellen *Sie eine .vsix-Datei* manuell:

   1. Erstellen Sie die Datei *extension.vsixmanifest* und die Datei *[Content_Types].xml* in einem neuen Ordner. Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

   2. Klicken Sie im Windows Explorer mit der rechten Maustaste auf den Ordner, der die beiden XML-Dateien enthält, klicken Sie auf **Senden an**, und klicken Sie dann auf Komprimierter (gezippter) Ordner. Benennen Sie die resultierende *ZIP-Datei* in *Filename.vsix*um, wobei Filename der Name der verteilbaren Datei ist, die Ihr Paket installiert.

Damit Visual Studio eine Startseite `Content Element` erkennt, muss das VSIX-Manifest eine `CustomExtension Element` enthalten, für die das `Type` Attribut auf `"StartPage"`festgelegt ist. Eine Startseitenerweiterung, die mithilfe der VSIX-Bereitstellung installiert wurde, wird in der Liste **Startseite anpassen** auf der Seite **Startoptionen** als **[Installierte Erweiterungs]-Erweiterungsname** *Extension Name*angezeigt.

Wenn Ihr Startpage-Paket Assemblys enthält, müssen Sie eine Bindungspfadregistrierung hinzufügen, damit sie beim Start von Visual Studio verfügbar sind. Stellen Sie hierzu sicher, dass Ihr Paket eine *Pkgdef-Datei* mit den folgenden Informationen enthält.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>VSIX-Bereitstellung für alle Benutzer
 Standardmäßig werden in VSIX-Paketen bereitgestellte Erweiterungen nur für den aktuellen Benutzer installiert. Sie können eine Startseite für alle Benutzer des Zielcomputers installieren, indem Sie eine All-Users-Bereitstellung erstellen.

### <a name="to-create-an-all-users-deployment"></a>So erstellen Sie eine All-User-Bereitstellung

1. Öffnen Sie die Datei *extension.vsixmanifest* in der Codeansicht.

2. Fügen `Identifier` Sie im Element des vsix-Manifests `AllUsers` ein `true`Element mit dem Wert .

    ```
    <AllUsers>true</AllUsers>
    ```

     Dies bewirkt, dass das vsix-Installationsprogramm zur Eingabe von Administratorberechtigungen auffordert, und dann die Dateien in *"Common7"IDE-Erweiterungen*" installieren.

3. Öffnen Sie die *.pkgdef-Datei.*

4. Ändern Sie die *.pkgdef,* um die Standardstartseite unter HKLM festzulegen, indem Sie Folgendes hinzufügen, wobei *MyStartPage.xaml* der Name der *.xaml-Datei* ist, die Ihre Startseite enthält.

     [$RootKey-StartPage-Standard]

     "Uri"="$PackageFolder-\\*MyStartPage.xaml*"

     Dadurch wird Visual Studio aufgefordert, sich in der neuen Startseite zu suchen.

## <a name="file-copy-deployment"></a>Dateikopierbereitstellung
 Sie müssen keine *.vsix-Datei* erstellen, um eine benutzerdefinierte Startseite bereitzustellen. Stattdessen können Sie das Markup und die unterstützenden Dateien direkt in den <em>Ordner "StartPages"\* des Benutzers kopieren. Die Liste der*Startseiten</em> * auf der *.xaml* Seite **Startoptionen** wird zusammen mit dem Pfad aufgeführt, z. B. *%USERPROFILE%,Meine Dokumente,\\Visual Studio, "Version", "Startpages" "Dateiname" (Dateiname).* Wenn Ihre Startseite Verweise auf private Assemblys enthält, müssen Sie sie\* kopieren und in den Ordner *-PrivateAssemblies einfügen.

 Um eine Startseite zu verteilen, die Sie erstellt haben, ohne sie in einer *vSix-Datei* zu verpacken, empfehlen wir, eine grundlegende Dateikopierstrategie zu verwenden, z. B. ein Batchskript oder eine andere Bereitstellungstechnologie, mit der Sie die Dateien in den erforderlichen Verzeichnissen abspeichern können.

### <a name="to-manually-install-a-custom-start-page"></a>So installieren Sie manuell eine benutzerdefinierte Startseite

1. Kopieren Sie die *.xaml-Datei,* die das Startseitenmarkup enthält, zusammen mit allen unterstützenden Dateien\* außer Assemblys, und fügen Sie sie in den Ordner *-StartPages des Benutzers ein.

2. Wenn die Startseite Assemblys erfordert, kopieren Sie sie, und fügen Sie sie in *.. "Visual Studio-Installationsordner" ,,Common7'IDE'PrivateAssemblies '\\. \\*

3. Wählen Sie in der Liste **Startseite anpassen** auf der Seite **Startoptionen** die neue Startseite aus. Weitere Informationen finden Sie unter [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)
- [Hinzufügen von Benutzersteuerelementen zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
