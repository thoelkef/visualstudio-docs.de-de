---
title: Erstellen von ClickOnce-Anwendungen über die Befehlszeile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 183cb81798841c6640ea1b17d8db3820e0229769
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Erstellen von ClickOnce-Anwendungen über die Befehlszeile
In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], Sie können Projekte über die Befehlszeile erstellen, auch wenn sie in der integrierten Entwicklungsumgebung (IDE) erstellt werden. Tatsächlich können Sie ein mit erstelltes Projekt neu erstellen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] auf einem anderen Computer, die nur die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert. Dadurch können Sie einen Build mithilfe eines automatisierten Prozesses zu reproduzieren, z. B. in einem zentralen Build Labor- oder mithilfe von erweiterten Skripttechniken Gegenstand des beim Erstellen des Projekts selbst.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Verwenden von MSBuild für die Bereitstellung von ClickOnce-Anwendung zu reproduzieren.  
 Wenn Sie Msbuild über die Befehlszeile Veröffentlichungsordner, weist es das MSBuild-System erstellen Sie das Projekt und erstellen eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung im Ordner "Veröffentlichen". Dies entspricht dem Auswählen der **veröffentlichen** Befehl in der IDE.  
  
 Dieser Befehl führt msbuild.exe, die den Pfad in der Umgebung der Visual Studio-Eingabeaufforderungsfenster aktiviert ist.  
  
 Eine "Target" ist ein Indikator für MSBuild zum Verarbeiten des Befehls. Die wichtigsten Ziele sind das Ziel "Build" und das Ziel "Veröffentlichen". Das Build-Ziel ist das Äquivalent zur Auswahl des Builds Befehlsklasse (oder drücken Sie F5) in der IDE. Wenn Sie das Projekt erstellen möchten, können Sie, die erreichen, indem Sie eingeben `msbuild`. Dieser Befehl funktioniert, da das Build-Ziel als Standardziel für alle Projekte, die von generiert ist [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Dies bedeutet, dass Sie nicht explizit benötigen, geben Sie das Build-Ziel. Aus diesem Grund eingeben `msbuild` ist der gleiche Vorgang als Eingabe `msbuild /target:build`.  
  
 Die `/target:publish` weist MSBuild an das Veröffentlichungsziel aufrufen. Das Veröffentlichungsziel hängt von der Build-Ziel. Dies bedeutet, dass der Veröffentlichungsvorgang eine Obermenge der Erstellungsvorgang ist. Beispielsweise, wenn Sie eine Änderung an einer Visual Basic- oder C#-Quelldateien vorgenommen haben, würden die entsprechende Assembly automatisch durch den Veröffentlichungsvorgang neu erstellt werden.  
  
 Informationen zum Generieren einer vollständiges [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung verwenden das Befehlszeilentool "Mage.exe" zum Erstellen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifest, finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Erstellen und das Erstellen einer einfachen ClickOnce-Anwendung mithilfe von MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Zum Erstellen und Veröffentlichen einer ClickOnce-Projekt  
  
1.  Klicken Sie auf **neues Projekt** aus der **Datei** Menü. Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie **Windows-Anwendung** und nennen Sie sie `CmdLineDemo`.  
  
3.  Aus der **erstellen** Menü klicken Sie auf die **veröffentlichen** Befehl.  
  
     Dadurch wird sichergestellt, dass das Projekt ordnungsgemäß konfiguriert ist, um in Form einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anwendungsbereitstellung.  
  
     Der Webpublishing-Assistent wird angezeigt.  
  
4.  Klicken Sie im Assistenten für das Veröffentlichen auf **Fertig stellen**.  
  
     Visual Studio generiert und zeigt die Standardwebseite Publish.htm aufgerufen.  
  
5.  Speichern Sie das Projekt, und notieren Sie sich den Speicherort des Ordners, in dem es gespeichert ist.  
  
 Die oben genannten Schritte zum Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Projekt, das zum ersten Mal veröffentlicht wurde. Jetzt können Sie den Build außerhalb der IDE reproduzieren.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Reproduzieren Sie den Build in der Befehlszeile  
  
1.  Beenden Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Vom Windows **starten** Menü klicken Sie auf **Programme**, klicken Sie dann **Microsoft Visual Studio**, klicken Sie dann **Visual Studio-Tools**, dann **Visual Studio-Eingabeaufforderung**. Dies sollte eine Eingabeaufforderung öffnen Sie im Stammordner des aktuellen Benutzers.  
  
3.  In der **Visual Studio-Eingabeaufforderung**, ändern Sie das aktuelle Verzeichnis auf den Speicherort des Projekts, die Sie soeben erstellt haben über. Geben Sie z. B. `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  So entfernen Sie die vorhandenen Dateien in erstellten "zum Erstellen und Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Projekt" Typ `rmdir /s publish`.  
  
     Dieser Schritt ist optional, aber es wird sichergestellt, dass die neuen Dateien von der Befehlszeile erstellt wurden.  
  
5.  Geben Sie `msbuild /target:publish` ein.  
  
 Die oben genannten Schritte erzeugt eine vollständige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anwendungsbereitstellung in einem Unterordner des Projekts mit dem Namen P**veröffentlichen**. CmdLineDemo.application ist die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest. Der Ordner CmdLineDemo_1.0.0.0 enthält die Dateien CmdLineDemo.exe und CmdLineDemo.exe.manifest, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Setup.exe ist der Bootstrapper, den standardmäßig dafür konfiguriert ist, installieren Sie die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Der Ordner enthält die verteilbaren Komponenten für die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Dies ist der gesamte Satz von Dateien, die Sie die Anwendung über das Internet oder über die UNC oder der CD/DVD bereitstellen müssen.  
  
## <a name="publishing-properties"></a>Veröffentlichungseigenschaften  
 Beim Veröffentlichen der Anwendung in der oben beschriebenen Verfahren werden die folgenden Eigenschaften in der Projektdatei, durch den Veröffentlichungs-Assistenten eingefügt. Diese Eigenschaften direkt zu beeinflussen wie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung wird erstellt.  
  
 In CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
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
  
 Sie können eine dieser Eigenschaften in der Befehlszeile überschreiben, ohne Ändern der Projektdatei selbst. Beispielsweise werden die folgenden erstellen die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung ohne die Bootstrapper-Anwendung:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Veröffentlichungseigenschaften werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus der **veröffentlichen**, **Sicherheit**, und **Signierung** Eigenschaftenseiten der **Projekt-Designer** . Im folgenden finden Sie eine Beschreibung für die publishing Eigenschaften werden zusammen mit Angabe der wie jede in den verschiedenen Eigenschaftenseiten im Anwendungs-Designer festgelegt wird:  
  
-   `AssemblyOriginatorKeyFile` Bestimmt die Schlüsseldatei zum Signieren verwendet Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifeste. Dieser Schlüssel kann auch verwendet werden, Ihre Assemblys einen starken Namen zuweisen. Diese Eigenschaft wird festgelegt, auf die **Signierung** auf der Seite der **Projekt-Designer**.  
  
 Die folgenden Eigenschaften werden festgelegt, auf die **Sicherheit** Seite:  
  
-   **Aktivieren von ClickOnce-Sicherheitseinstellungen** bestimmt, ob [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste generiert werden. Wenn ein Projekt erstmalig erstellt wird, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Generierung von Manifesten ist standardmäßig deaktiviert. Der Assistent wird automatisch aktivieren Sie dieses Flag auf, wenn Sie zum ersten Mal veröffentlichen.  
  
-   **TargetZone** bestimmt die Ebene der Vertrauenswürdigkeit in ausgegeben werden Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Mögliche Werte sind "Internet", "LocalIntranet" und "Benutzerdefiniert". Internet und LocalIntranet dazu führen, dass einen Standardberechtigungssatz in ausgegeben werden Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. LocalIntranet ist die Standardeinstellung und bedeutet im Grunde volle Vertrauenswürdigkeit. Benutzerdefinierte gibt an, dass nur die Berechtigungen, die in der Datei "Basis" app.manifest "explizit angegebener in ausgegeben werden die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Die Datei "app.manifest" wird eine partielle Manifestdatei, die nur die Definitionen der Vertrauensstellung Informationen enthält. Es ist eine versteckte Datei, die dem Projekt automatisch hinzugefügt, beim Konfigurieren von Berechtigungen für die **Sicherheit** Seite.  
  
 Die folgenden Eigenschaften werden festgelegt, auf die **veröffentlichen** Seite:  
  
-   `PublishUrl` ist der Speicherort in der IDE, in dem die Anwendung veröffentlicht wird. Erfolgt dieses einfügen in die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsmanifest, wenn weder die `InstallUrl` oder `UpdateUrl` -Eigenschaft angegeben wird.  
  
-   `ApplicationVersion` Gibt die Version des der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dies ist eine vierstellige Versionsnummer. Wenn die letzte Ziffer ist eine "*", und dann die `ApplicationRevision` für den Wert in das Manifest eingefügt wird, während des Buildvorgangs ersetzt wird.  
  
-   `ApplicationRevision` Gibt die Version an. Dies ist eine Ganzzahl, die jedes Mal inkrementiert, die Sie in der IDE zu veröffentlichen. Beachten Sie, dass für Builds ausgeführt werden, in der Befehlszeile nicht automatisch erhöht wird.  
  
-   `Install` Bestimmt, ob die Anwendung eine installierte Anwendung oder eine Anwendung aus der Web ausgeführt wird.  
  
-   `InstallUrl` (nicht dargestellt) ist der Speicherort, in dem Benutzer die Anwendung installiert wird. Wenn angegeben, wird dieser Wert in den setup.exe-Bootstrapper geschrieben, wenn die `IsWebBootstrapper` -Eigenschaft aktiviert ist. Auch in der Anwendung manifest If eingefügt der `UpdateUrl` nicht angegeben wird.  
  
-   `SupportUrl` (nicht dargestellt) ist der Speicherort in verknüpft die **Programme hinzufügen/entfernen** im Dialogfeld für eine installierte Anwendung.  
  
 Die folgenden Eigenschaften werden festgelegt, der **Anwendungsupdates** (Dialogfeld), auf das Sie über die **veröffentlichen** Seite.  
  
-   `UpdateEnabled` Gibt an, ob die Anwendung auf Updates überprüfen soll.  
  
-   `UpdateMode` Gibt an, Updates Vorder- oder Hintergrund Updates.  
  
-   `UpdateInterval` Gibt an, wie häufig die Anwendung nach Updates suchen soll.  
  
-   `UpdateIntervalUnits` Gibt an, ob die `UpdateInterval` Wert wird in Stunden, Tage oder Wochen.  
  
-   `UpdateUrl` (nicht dargestellt) ist der Speicherort, von dem die Anwendung Updates empfangen werden. Wenn angegeben, wird dieser Wert in das Anwendungsmanifest eingefügt.  
  
-   Die folgenden Eigenschaften werden festgelegt, der **Veröffentlichungsoptionen** (Dialogfeld), auf das Sie über die **veröffentlichen** Seite.  
  
-   `PublisherName` Gibt den Namen des Verlegers beim Installieren oder Ausführen der Anwendung angezeigt. Bei einer installierten Anwendung er dient außerdem zum Geben Sie den Namen des Ordners auf dem **starten** Menü.  
  
-   `ProductName` Gibt den Namen des Produkts, die beim Installieren oder Ausführen der Anwendung angezeigt. Bei einer installierten Anwendung er dient außerdem zum Geben Sie den Namen der Verknüpfung auf der **starten** Menü.  
  
-   Die folgenden Eigenschaften werden festgelegt, der **Voraussetzungen** (Dialogfeld), auf das Sie über die **veröffentlichen** Seite.  
  
-   `BootstrapperEnabled` Bestimmt, ob die setup.exe-Bootstrapper generiert.  
  
-   `IsWebBootstrapper` Bestimmt, ob der setup.exe-Bootstrapper über das Internet oder in datenträgerbasierte Modus funktioniert.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl "publishUrl" und UpdateURL  
 Die folgende Tabelle zeigt die vier URL-Optionen für die ClickOnce-Bereitstellung.  
  
|URL-option|Beschreibung|  
|----------------|-----------------|  
|`PublishURL`|Erforderlich, wenn Sie die ClickOnce-Anwendung auf einer Website veröffentlichen.|  
|`InstallURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn der Standort für die Installation unterscheidet, wird die `PublishURL`. Angenommen, Sie legen konnte die `PublishURL` auf einem FTP-Pfad und der `InstallURL` auf eine Web-URL.|  
|`SupportURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn die Support-Website unterscheidet, wird die `PublishURL`. Sie können z. B. Festlegen der `SupportURL` auf Ihr Unternehmen Customer Support-Website.|  
|`UpdateURL`|Dies ist optional. Legen Sie diese URL-Option aus, wenn der Updatepfad unterscheidet die `InstallURL`. Angenommen, Sie legen konnte die `PublishURL` auf einem FTP-Pfad und der `UpdateURL` auf eine Web-URL.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)