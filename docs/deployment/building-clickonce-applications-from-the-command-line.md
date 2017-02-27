---
title: "Building ClickOnce Applications from the Command Line | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, from command line"
  - "publishing"
  - "publishing, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Building ClickOnce Applications from the Command Line
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] können Sie Projekte über die Befehlszeile erstellen, auch wenn diese mit der integrierten Entwicklungsumgebung \(IDE\) erstellt werden.  Sie können sogar ein mit [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] erstelltes Projekt auf einem anderen Computer neu erstellen, auf dem lediglich [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert ist.  Dadurch kann ein Build mithilfe eines automatisierten Vorgangs reproduziert werden, beispielsweise in einer zentralen Kompilierungsstelle oder mit erweiterten Skripttechniken, die selbst über den Erstellungsumfang des Projekts hinausgehen.  
  
## Reproduzieren von ClickOnce\-Anwendungsbereitstellungen mit MSBuild  
 Wenn Sie an der Befehlszeile "msbuild \/target:publish" ausführen, wird das MSBuild\-System angewiesen, das Projekt zu erstellen und im Veröffentlichungsordner eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung zu erstellen.  Dies hat den gleichen Effekt wie der Befehl **Veröffentlichen** in der IDE.  
  
 Durch diesen Befehl wird das Programm msbuild.exe ausgeführt, das sich im Pfad der Eingabeaufforderungsumgebung von Visual Studio befindet.  
  
 Der Parameter "target" \(Ziel\) weist MSBuild an, wie der Befehl verarbeitet wird.  Die wichtigsten Ziele sind "build" und "publish".  Das Buildziel entspricht in der IDE dem Befehl Erstellen \(TASTE F5\).  Wenn Sie das Projekt nur erstellen möchten, können Sie einfach `msbuild`eingeben.  Dieser Befehl ist zulässig, da das Buildziel für alle mit [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] generierten Projekte das Standardziel ist.  Dies bedeutet, dass Sie das Buildziel nicht explizit angeben müssen.  Deshalb entspricht der Befehl `msbuild` dem Befehl `msbuild /target:build`.  
  
 Der `/target:publish`\-Parameter weist MSBuild an, das Publishziel aufzurufen.  Das Publishziel ist abhängig vom Buildziel.  Das heißt, dass der Publishvorgang dem Buildvorgang übergeordnet ist.  Wenn Sie beispielsweise eine der Visual Basic\- oder C\#\-Quelldateien geändert haben, wird durch den Publishvorgang die entsprechende Assembly automatisch neu erstellt.  
  
 Weitere Informationen zum Generieren einer vollständigen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung mit dem Befehlszeilentool Mage.exe zum Erstellen eines [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifests finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Erstellen einer einfachen ClickOnce\-Anwendung mit MSBuild  
  
#### So erstellen und veröffentlichen Sie ein ClickOnce\-Projekt  
  
1.  Klicken Sie im Menü **Datei** auf **Neues Projekt**.  Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie **Windows\-Anwendung** aus, und geben Sie dieser den Namen `CmdLineDemo`.  
  
3.  Klicken Sie im Menü **Erstellen** auf den Befehl **Veröffentlichen**.  
  
     Mit diesem Schritt stellen Sie sicher, dass das Projekt ordnungsgemäß für das Erzeugen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsbereitstellung konfiguriert ist.  
  
     Der Webpublishing\-Assistent wird angezeigt.  
  
4.  Klicken Sie im Webpublishing\-Assistenten auf **Fertig stellen**.  
  
     Visual Studio generiert die Standardwebseite Publish.htm und zeigt diese an.  
  
5.  Speichern Sie das Projekt, und notieren Sie sich seinen Speicherort.  
  
 Durch die oben beschriebene Vorgehensweise wird ein neu veröffentlichtes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Projekt erstellt.  Nun können Sie den Build außerhalb der IDE reproduzieren.  
  
#### So reproduzieren Sie den Build über die Befehlzeile  
  
1.  Beenden Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Klicken Sie in Windows im Menü **Start** auf **Alle Programme**, klicken Sie dann auf **Microsoft Visual Studio** und **Visual Studio\-Tools**, und klicken Sie anschließend auf **Visual Studio\-Eingabeaufforderung**.  Dadurch wird im Stammordner des aktuellen Benutzers eine Eingabeaufforderung geöffnet.  
  
3.  Wechseln Sie an der **Visual Studio\-Eingabeaufforderung** vom aktuellen Verzeichnis zum Speicherort des eben erstellten Projekts.  Geben Sie z. B. `chdir Eigene Dateien\Visual Studio\Projects\CmdLineDemo` ein.  
  
4.  Zum Löschen der im Abschnitt "So erstellen und veröffentlichen Sie ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Projekt" erstellten Dateien geben Sie `rmdir /s publish` ein.  
  
     Dieser Schritt ist optional, stellt jedoch sicher, dass die neuen Dateien alle von der Befehlszeile erstellt wurden.  
  
5.  Geben Sie `msbuild /target:publish` ein.  
  
 Durch die oben beschriebenen Schritte wird in einem Unterordner des Projekts mit dem Namen **Publish** eine vollständige [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsbereitstellung erstellt.  CmdLineDemo.application ist das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest.  Der Ordner CmdLineDemo\_1.0.0.0 enthält die Dateien CmdLineDemo.exe und CmdLineDemo.exe.manifest, das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest.  Setup.exe ist der Bootstrapper, durch den standardmäßig [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert wird.  Der Ordner DotNetFX enthält die verteilbaren Komponenten für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Dies sind alle Dateien, die Sie für die Bereitstellung der Anwendung über das Web, einen UNC\-Pfad oder CD\/DVD benötigen.  
  
## Veröffentlichungseigenschaften  
 Nach Veröffentlichen der Anwendung mit der oben beschriebenen Vorgehensweise werden durch den Webpublishing\-Assistenten die folgenden Eigenschaften in die Projektdatei eingefügt.  Diese Eigenschaften beeinflussen direkt die Art und Weise der Erzeugung der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
 In CmdLineDemo.vbproj \/ CmdLineDemo.csproj:  
  
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
  
 Sie können diese Eigenschaften an der Befehlszeile überschreiben, ohne die Projektdatei selbst zu ändern.  Beispielsweise erstellt der folgende Befehl eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsbereitstellung ohne Bootstrapper:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Veröffentlichungseigenschaften werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] im **Projekt\-Designer** auf den Eigenschaftenseiten **Veröffentlichen**, **Sicherheit** und **Signierung** verwaltet.  Im Folgenden finden Sie eine Beschreibung der Veröffentlichungseigenschaften zusammen mit einem Hinweis, wie diese im Anwendungs\-Designer auf den verschiedenen Eigenschaftenseiten festgelegt werden.  
  
-   Durch `AssemblyOriginatorKeyFile` wird die Schlüsseldatei festgelegt, die zur Signierung der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifeste verwendet wird.  Derselbe Schlüssel kann auch verwendet werden, um Assemblys einen starken Namen zuzuweisen.  Diese Eigenschaft wird im **Projekt\-Designer** auf der Seite **Signierung** festgelegt.  
  
 Auf der Seite **Sicherheit** werden die folgenden Eigenschaften festgelegt:  
  
-   Durch **ClickOnce\-Sicherheitseinstellungen aktivieren** wird bestimmt, ob [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifeste generiert werden.  Wenn ein Projekt erstmalig erstellt wird, ist die Generierung von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifesten standardmäßig deaktiviert.  Bei der ersten Veröffentlichung wird dieser Flag durch den Assistenten automatisch aktiviert.  
  
-   Durch **TargetZone** wird die Vertrauenswürdigkeitsstufe festgelegt, die für das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest ausgegeben wird.  Mögliche Werte sind "Internet", "LocalIntranet" und "Custom".  Durch die Werte Internet und LocalIntranet wird ein Standardberechtigungssatz in das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest ausgegeben.  LocalIntranet ist der Standardwert und steht im Grunde für volle Vertrauenswürdigkeit.  Durch Festlegen von Custom \(Benutzerdefiniert\) werden nur die in der Basisdatei app.manifest explizit angegebenen Berechtigungen an das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest ausgegeben.  Die Datei app.manifest ist eine partielle Manifestdatei, die nur die Vertrauenswürdigkeitsdefinitionen enthält.  Es handelt sich um eine versteckte Datei, die dem Projekt automatisch hinzugefügt wird, wenn Sie auf der Seite **Sicherheit** Berechtigungen konfigurieren.  
  
 Auf der Seite **Veröffentlichen** werden die folgenden Eigenschaften festgelegt:  
  
-   `PublishUrl` ist der Speicherort in der IDE, an dem die Anwendung veröffentlicht wird.  Dieser wird in das [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest eingefügt, wenn weder die `InstallUrl`\-Eigenschaft noch die `UpdateUrl`\-Eigenschaft angegeben ist.  
  
-   `ApplicationVersion` gibt die Version der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung an.  Dies ist eine vierstellige Versionsnummer.  Wenn die letzte Stelle ein "\*" ist, wird `ApplicationRevision` durch den zur Buildzeit in das Manifest eingefügten Wert ersetzt.  
  
-   `ApplicationRevision` gibt die Revisionsnummer an.  Dies ist eine ganze Zahl, die jedes Mal erhöht wird, wenn in der IDE veröffentlicht wird.  Beachten Sie, dass diese nicht automatisch für Builds erhöht wird, die an der Befehlszeile ausgeführt werden.  
  
-   Durch `Install` wird festgelegt, ob es sich um eine installierte Anwendung handelt, oder um eine Anwendung, die über das Web ausgeführt wird.  
  
-   `InstallUrl` \(nicht angezeigt\) ist der Speicherort, von dem Benutzer die Anwendung installieren.  Wenn dieser Wert angegeben ist, wird bei aktivierter `IsWebBootstrapper`\-Eigenschaft dieser Wert in den Setup.exe\-Bootstrapper geschrieben.  Auch wenn kein `UpdateUrl` angegeben ist, wird er in das Anwendungsmanifest eingefügt.  
  
-   `SupportUrl` \(nicht angezeigt\) ist der Speicherort für eine installierte Anwendung, auf den die Verknüpfung im Dialogfeld **Software** verweist.  
  
 Die folgenden Eigenschaften werden auf der Seite **Veröffentlichen** im Dialogfeld **Anwendungsupdates** festgelegt.  
  
-   Durch `UpdateEnabled` wird festgelegt, ob die Anwendung nach Updates sucht.  
  
-   Durch `UpdateMode` wird festgelegt, ob die Updates im Vordergrund oder im Hintergrund erfolgen.  
  
-   `UpdateInterval` gibt die Häufigkeit von Überprüfungen auf Updates an.  
  
-   `UpdateIntervalUnits` zeigt an, ob der `UpdateInterval`\-Wert in Einheiten von Stunden, Tagen oder Wochen angegeben ist.  
  
-   `UpdateUrl` \(nicht angezeigt\) ist der Speicherort, von dem die Anwendung die Updates abruft.  Dieser Wert wird in das Anwendungsmanifest eingefügt, wenn er angegeben wurde.  
  
-   Die folgenden Eigenschaften werden über die Seite **Veröffentlichen** im Dialogfeld **Veröffentlichungsoptionen** festgelegt.  
  
-   `PublisherName` gibt den Namen des Herausgebers an, der bei Installation oder Ausführen der Anwendung angezeigt wird.  Bei einer installierten Anwendung gibt dieser Wert auch den Namen des Ordners im **Startmenü** an.  
  
-   `ProductName` gibt den Namen des Produkts an, der bei Installation oder Ausführen der Anwendung angezeigt wird.  Bei einer installierten Anwendung gibt dieser Wert auch den Namen der Verknüpfung im **Startmenü** an.  
  
-   Die folgenden Eigenschaften werden über die Seite **Veröffentlichen** im Dialogfeld **Erforderliche Komponenten** festgelegt.  
  
-   Durch `BootstrapperEnabled` wird festgelegt, ob der Setup.exe\-Bootstrapper generiert wird.  
  
-   Durch `IsWebBootstrapper` wird festgelegt, ob der Setup.exe\-Bootstrapper über das Web oder einen lokalen Datenträger ausgeführt wird.  
  
## InstallURL, SupportUrl, PublishURL und UpdateURL  
 In der folgenden Tabelle sind die vier URL\-Optionen für die ClickOnce\-Bereitstellung angegeben.  
  
|URL\-Option|Beschreibung|  
|-----------------|------------------|  
|`PublishURL`|Erforderlich, wenn Sie die ClickOnce\-Anwendung auf einer Website veröffentlichen.|  
|`InstallURL`|Optional.  Legen Sie diese URL\-Option fest, wenn sich die Installationssite von `PublishURL` unterscheidet.  Sie könnten beispielsweise für den `PublishURL` einen FTP\-Pfad verwenden, und für den `InstallURL` einen Web\-URL.|  
|`SupportURL`|Optional.  Legen Sie diese URL\-Option fest, wenn sich die Supportsite von `PublishURL` unterscheidet.  Sie können `SupportURL` z. B. auf die Kundendienst\-Website Ihres Unternehmens festlegen.|  
|`UpdateURL`|Optional.  Legen Sie diese URL\-Option fest, wenn sich der Updatespeicherort von `InstallURL` unterscheidet.  Sie könnten beispielsweise für den `PublishURL` einen FTP\-Pfad verwenden, und für den `UpdateURL` einen Web\-URL.|  
  
## Siehe auch  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)