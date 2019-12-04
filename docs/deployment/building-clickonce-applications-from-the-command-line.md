---
title: Entwickeln von ClickOnce-Anwendungen über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797204"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Erstellen von ClickOnce-Anwendungen über die Befehlszeile
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]können Sie Projekte von der Befehlszeile aus erstellen, auch wenn Sie in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) erstellt werden. Tatsächlich können Sie ein Projekt, das mit [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] erstellt wurde, auf einem anderen Computer neu erstellen, auf dem nur die .NET Framework installiert ist. Dadurch können Sie einen Build mithilfe eines automatisierten Prozesses reproduzieren, z. b. in einem zentralen buildlab oder mithilfe erweiterter Skript Erstellungs Verfahren, die über den Umfang der Erstellung des Projekts hinausgehen.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>Verwenden von MSBuild zum Reproduzieren von ClickOnce-Anwendungs Bereitstellungen
 Wenn Sie MSBuild/target: Publish in der Befehlszeile aufrufen, wird das MSBuild-System aufgefordert, das Projekt zu erstellen und im Veröffentlichungs Ordner eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung zu erstellen. Dies entspricht der Auswahl des Befehls **Publish** in der IDE.

 Dieser Befehl führt *MSBuild. exe*aus, das sich auf dem Pfad in der Visual Studio-Eingabe Aufforderungs Umgebung befindet.

 Ein "Ziel" ist ein Indikator für MSBuild zum Verarbeiten des Befehls. Die wichtigsten Ziele sind das Build-Ziel und das "Publish"-Ziel. Das Buildziel entspricht dem Auswählen des Build-Befehls (oder Drücken von F5) in der IDE. Wenn Sie nur das Projekt erstellen möchten, können Sie dies erreichen, indem Sie `msbuild`eingeben. Dieser Befehl funktioniert, da das Build-Ziel das Standardziel für alle Projekte ist, die von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]generiert werden. Dies bedeutet, dass Sie das Buildziel nicht explizit angeben müssen. Daher ist das Eingeben von `msbuild` der gleiche Vorgang wie das Eingeben von `msbuild /target:build`.

 Der `/target:publish` Befehl weist MSBuild an, das Veröffentlichungsziel aufzurufen. Das Veröffentlichungsziel hängt vom Buildziel ab. Dies bedeutet, dass der Veröffentlichungs Vorgang eine supermenge des Buildvorgangs ist. Wenn Sie z. b. eine Änderung an einer Visual Basic-oder C# Quelldatei vorgenommen haben, wird die entsprechende Assembly automatisch durch den Veröffentlichungs Vorgang neu erstellt.

 Informationen zum Erstellen einer vollständigen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung mit dem Befehlszeilen Tool "Mage. exe" zum Erstellen des [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifests finden Sie unter Exemplarische Vorgehensweise [: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>Erstellen und Erstellen einer einfachen ClickOnce-Anwendung mit MSBuild

#### <a name="to-create-and-publish-a-clickonce-project"></a>So erstellen und veröffentlichen Sie ein ClickOnce-Projekt

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

    Wählen Sie die Projektvorlage **Windows-Desktop Anwendung** aus, und benennen Sie das Projekt `CmdLineDemo`.

1. Klicken Sie im Menü **Erstellen** auf den Befehl **veröffentlichen** .

    Mit diesem Schritt wird sichergestellt, dass das Projekt ordnungsgemäß für die Erstellung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Bereitstellung konfiguriert ist.

    Der Veröffentlichungs-Assistent wird angezeigt.

1. Klicken Sie im Veröffentlichungs-Assistenten auf **Fertig**stellen.

    Visual Studio generiert und zeigt die Standard Webseite mit dem Namen *Publish. htm*an.

1. Speichern Sie Ihr Projekt, und notieren Sie sich den Speicherort des Ordners, in dem er gespeichert ist.

   In den obigen Schritten wird ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Projekt erstellt, das zum ersten Mal veröffentlicht wurde. Nun können Sie den Build außerhalb der IDE reproduzieren.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>So reproduzieren Sie den Build über die Befehlszeile

1. Beenden Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Klicken Sie im Windows- **Startmenü** auf **Alle Programme**, dann auf **Microsoft Visual Studio**und dann auf **Visual Studio-Tools**und dann auf **Visual Studio-Eingabeaufforderung**. Dadurch sollte eine Eingabeaufforderung im Stamm Ordner des aktuellen Benutzers geöffnet werden.

3. Ändern Sie in der **Visual Studio-Eingabeaufforderung**das aktuelle Verzeichnis in den Speicherort des Projekts, das Sie gerade erstellt haben. Geben Sie beispielsweise `chdir My Documents\Visual Studio\Projects\CmdLineDemo` ein.

4. Um die vorhandenen Dateien zu entfernen, die in "So erstellen und veröffentlichen Sie ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Projekt" erstellt haben, geben Sie `rmdir /s publish`ein.

    Dieser Schritt ist optional, stellt jedoch sicher, dass alle neuen Dateien vom Befehlszeilenbuild erstellt wurden.

5. Geben Sie `msbuild /target:publish` ein.

   In den obigen Schritten wird eine vollständige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Bereitstellung in einem Unterordner des Projekts mit dem Namen **veröffentlichen**erzeugt. *CmdLineDemo. Application* ist das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungs Manifest. Der Ordner *CmdLineDemo_1.0.0.0* enthält die Dateien *CmdLineDemo. exe* und *CmdLineDemo. exe. Manifest*, das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest. *Setup. exe* ist der Boots Trapper, der standardmäßig für die Installation des .NET Framework konfiguriert ist. Der Dotnetfx-Ordner enthält die verteilbaren Dateien für die .NET Framework. Dies ist der gesamte Satz von Dateien, die Sie benötigen, um Ihre Anwendung über das Web oder über UNC oder CD/DVD bereitzustellen.
   
> [!NOTE]
> Das MSBuild-System verwendet die Option **PublishDir** , um den Speicherort für die Ausgabe anzugeben, z. b. `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Eigenschaften veröffentlichen
 Wenn Sie die Anwendung in den oben aufgeführten Prozeduren veröffentlichen, werden die folgenden Eigenschaften durch den Veröffentlichungs-Assistenten in die Projektdatei eingefügt. Diese Eigenschaften beeinflussen direkt die Art und Weise, wie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung erstellt wird.

 Unter *CmdLineDemo.vbproj* / *CmdLineDemo.csproj* ist Folgendes möglich:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Sie können diese Eigenschaften in der Befehlszeile überschreiben, ohne die Projektdatei selbst zu ändern. Im folgenden Beispiel wird die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Bereitstellung ohne den Boots Trapper erstellt:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Veröffentlichungs Eigenschaften werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] von den Eigenschaften Seiten **veröffentlichen**, **Sicherheit**und **Signierung** des Projekt- **Designers**gesteuert. Im folgenden finden Sie eine Beschreibung der Veröffentlichungs Eigenschaften sowie einen Hinweis darauf, wie die einzelnen Eigenschaften Seiten des Anwendungs-Designers festgelegt werden:

- `AssemblyOriginatorKeyFile` bestimmt die Schlüsseldatei, die zum Signieren Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifeste verwendet wird. Derselbe Schlüssel kann auch verwendet werden, um Ihren Assemblys einen starken Namen zuzuweisen. Diese Eigenschaft wird auf der Seite **Signierung** des **Projekt-Designers**festgelegt.

  Die folgenden Eigenschaften werden auf der Seite **Sicherheit** festgelegt:

- **ClickOnce-Sicherheitseinstellungen aktivieren** bestimmt, ob [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste generiert werden. Wenn ein Projekt erstmalig erstellt wird, ist die Generierung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifests standardmäßig deaktiviert. Der Assistent schaltet dieses Flag automatisch ein, wenn Sie zum ersten Mal veröffentlichen.

- **TargetZone** bestimmt die Vertrauens Ebene, die in Ihrem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest ausgegeben werden soll. Mögliche Werte sind "Internet", "LocalIntranet" und "Custom". Internet und LocalIntranet bewirken, dass ein Standard Berechtigungs Satz in das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest ausgegeben wird. "LocalIntranet" ist die Standardeinstellung, und es bedeutet im Grunde, dass volle Vertrauenswürdigkeit Custom gibt an, dass nur die Berechtigungen, die in der Basisdatei " *app. Manifest* " explizit angegeben werden, in das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest ausgegeben werden sollen. Die Datei " *app. Manifest* " ist eine partielle Manifest-Datei, die nur die Definitionen der Vertrauens Informationen enthält. Dabei handelt es sich um eine versteckte Datei, die dem Projekt automatisch hinzugefügt wird, wenn Sie Berechtigungen auf der Seite **Sicherheit** konfigurieren.

  Die folgenden Eigenschaften werden auf der Seite " **veröffentlichen** " festgelegt:

- `PublishUrl` ist der Speicherort, in dem die Anwendung in der IDE veröffentlicht wird. Sie wird in das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungs Manifest eingefügt, wenn weder die `InstallUrl`-noch die `UpdateUrl`-Eigenschaft angegeben ist.

- `ApplicationVersion` gibt die Version der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung an. Dies ist eine vierstellige Versionsnummer. Wenn die letzte Ziffer "*" ist, wird der `ApplicationRevision` durch den Wert ersetzt, der zum Zeitpunkt der Erstellung in das Manifest eingefügt wird.

- `ApplicationRevision` die Revision angibt. Dies ist eine ganze Zahl, die jedes Mal erhöht wird, wenn Sie in der IDE veröffentlichen. Beachten Sie, dass es für Builds, die an der Befehlszeile ausgeführt werden, nicht automatisch inkrementiert wird.

- `Install` bestimmt, ob es sich bei der Anwendung um eine installierte Anwendung oder eine run-from-Web-Anwendung handelt.

- `InstallUrl` (nicht angezeigt) ist der Speicherort, von dem aus die Benutzer die Anwendung installieren. Wenn dieser Wert angegeben wird, wird dieser Wert in den Boots Trapper " *Setup. exe* " gebrannt, wenn die `IsWebBootstrapper`-Eigenschaft aktiviert ist. Sie wird auch in das Anwendungs Manifest eingefügt, wenn die `UpdateUrl` nicht angegeben ist.

- `SupportUrl` (nicht angezeigt) ist der Speicherort **, der im Dialogfeld** "Software" für eine installierte Anwendung verknüpft ist.

  Die folgenden Eigenschaften werden im Dialogfeld **Anwendungs Updates** festgelegt, auf das Sie über die Seite **veröffentlichen** zugreifen können.

- `UpdateEnabled` gibt an, ob die Anwendung nach Updates suchen soll.

- `UpdateMode` gibt entweder Vordergrund-oder Hintergrund Aktualisierungen an.

- `UpdateInterval` gibt an, wie häufig die Anwendung nach Updates suchen soll.

- `UpdateIntervalUnits` gibt an, ob der `UpdateInterval` Wert Stunden-, Tages-oder Wochen Einheiten entspricht.

- `UpdateUrl` (nicht angezeigt) ist der Speicherort, von dem die Anwendung Updates empfängt. Wenn angegeben, wird dieser Wert in das Anwendungs Manifest eingefügt.

  Die folgenden Eigenschaften werden im Dialogfeld **Veröffentlichungs Optionen** festgelegt, auf das Sie über die Seite **veröffentlichen** zugreifen können.

- `PublisherName` gibt den Namen des Verlegers an, der in der Eingabeaufforderung angezeigt wird, die beim Installieren oder Ausführen der Anwendung angezeigt wird. Im Fall einer installierten Anwendung wird Sie auch verwendet, um den Ordnernamen im **Startmenü** anzugeben.

- `ProductName` gibt den Namen des Produkts an, das in der Eingabeaufforderung angezeigt wird, die beim Installieren oder Ausführen der Anwendung angezeigt wird. Im Fall einer installierten Anwendung wird Sie auch verwendet, um den Verknüpfungs Namen im **Startmenü** anzugeben.

  Die folgenden Eigenschaften werden **im Dialogfeld** erforderliche Komponenten festgelegt, auf das Sie über die Seite **veröffentlichen** zugreifen können.

- `BootstrapperEnabled` bestimmt, ob der *Setup. exe* -Bootstrapper generiert werden soll.

- `IsWebBootstrapper` bestimmt, ob der *Setup. exe* -Boots Trapper über das Internet oder den Datenträger basierten Modus funktioniert.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL, and UpdateURL
 In der folgenden Tabelle sind die vier URL-Optionen für die ClickOnce-Bereitstellung aufgeführt.

|URL-Option|Beschreibung|
|----------------|-----------------|
|`PublishURL`|Erforderlich, wenn Sie die ClickOnce-Anwendung auf einer Website veröffentlichen.|
|`InstallURL`|Dies ist optional. Legen Sie diese URL-Option fest, wenn sich die Installations Site von der `PublishURL`unterscheidet. Beispielsweise können Sie die `PublishURL` auf einen FTP-Pfad festlegen und die `InstallURL` auf eine Web-URL festlegen.|
|`SupportURL`|Dies ist optional. Legen Sie diese URL-Option fest, wenn sich die Support Website von der `PublishURL`unterscheidet. Beispielsweise können Sie die `SupportURL` auf die Kundendienst Website Ihres Unternehmens festlegen.|
|`UpdateURL`|Dies ist optional. Legen Sie diese URL-Option fest, wenn sich der Update Speicherort vom `InstallURL`unterscheidet. Beispielsweise können Sie die `PublishURL` auf einen FTP-Pfad festlegen und die `UpdateURL` auf eine Web-URL festlegen.|

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce security and deployment (ClickOnce-Sicherheit und -Bereitstellung)](../deployment/clickonce-security-and-deployment.md)
- [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
