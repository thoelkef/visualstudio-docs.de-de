---
title: "How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce applications, multiple .NET Framework versions"
  - "ClickOnce deployment, multiple .NET Framework versions"
  - "deploying applications [ClickOnce], multiple .NET Framework versions"
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Use ClickOnce to Deploy Applications That Can Run on Multiple Versions of the .NET Framework
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Anwendung bereitstellen, die mithilfe der ClickOnce\-Bereitstellungstechnologie auf mehrere Versionen von .NET Framework abzielt.  Hierzu müssen Sie die Anwendungs\- und Bereitstellungsmanifeste generieren und aktualisieren.  
  
> [!NOTE]
>  Bevor Sie die Anwendung ändern, damit sie auf mehrere Versionen von .NET Framework abzielt, sollten Sie sicherstellen, dass Ihre Anwendung unter mehreren Versionen von .NET Framework ausgeführt werden kann.  Die Version der Common Language Runtime unterscheidet sich zwischen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] und .NET Framework 2.0, .NET Framework 3.0 und .NET Framework 3.5.  
  
 Dieser Prozess umfasst die folgenden Schritte:  
  
1.  Generieren der Anwendungs\- und Bereitstellungsmanifeste.  
  
2.  Ändern des Bereitstellungsmanifests, um mehrere .NET Framework\-Versionen aufzulisten.  
  
3.  Ändern der app.config\-Datei, um die kompatiblen .NET Framework\-Laufzeitversionen aufzulisten.  
  
4.  Ändern des Anwendungsmanifests, um abhängige Assemblys als .NET Framework\-Assemblys zu kennzeichnen.  
  
5.  Signieren des Anwendungsmanifests.  
  
6.  Aktualisieren und Signieren des Bereitstellungsmanifests.  
  
### So generieren Sie die Anwendungs\- und Bereitstellungsmanifeste  
  
-   Verwenden Sie den Veröffentlichungs\-Assistenten oder die Veröffentlichungsseite des Projekt\-Designers, um die Anwendung zu veröffentlichen und die Anwendungs\- und Bereitstellungsmanifestdateien zu generieren.  Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) oder [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md).  
  
### So ändern Sie das Bereitstellungsmanifest, um mehrere .NET Framework\-Versionen aufzulisten  
  
1.  Öffnen Sie im Veröffentlichungsverzeichnis das Bereitstellungsmanifest mit dem XML\-Editor in Visual Studio.  Das Bereitstellungsmanifest hat die Dateinamenerweiterung ".application".  
  
2.  Ersetzen Sie den XML\-Code zwischen den `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` und `</compatibleFrameworks>`\-Elementen durch XML, das die unterstützten .NET Framework\-Versionen für die Anwendung auflistet.  
  
     In der folgenden Tabelle werden einige der verfügbaren .NET Framework\-Versionen und das entsprechende XML aufgeführt, das Sie dem Bereitstellungsmanifest hinzufügen können.  
  
    |.NET Framework\-Version|XML|  
    |-----------------------------|---------|  
    |4 Client|\<framework targetVersion\="4.0" profile\="Client" supportedRuntime\="4.0.30319" \/\>|  
    |4 Full|\<framework targetVersion\="4.0" profile\="Full" supportedRuntime\="4.0.30319" \/\>|  
    |3.5 Client|\<framework targetVersion\="3.5" profile\="Client" supportedRuntime\="2.0.50727" \/\>|  
    |3.5 Full|\<framework targetVersion\="3.5" profile\="Full" supportedRuntime\="2.0.50727" \/\>|  
    |3.0|\<framework targetVersion\="3.0" supportedRuntime\="2.0.50727" \/\>|  
  
### So ändern Sie die app.config\-Datei, um die kompatiblen .NET Framework\-Laufzeitversionen aufzulisten  
  
1.  Öffnen Sie im Projektmappen\-Explorer die Datei "App.config" mit dem XML\-Editor in Visual Studio.  
  
2.  Ersetzen Sie den XML\-Code zwischen den `<startup>` und `</startup>`\-Elementen durch XML, das die unterstützten .NET Framework\-Laufzeiten für die Anwendung auflistet \(oder fügen Sie den XML\-Code hinzu\).  
  
     In der folgenden Tabelle werden einige der verfügbaren .NET Framework\-Versionen und das entsprechende XML aufgeführt, das Sie dem Bereitstellungsmanifest hinzufügen können.  
  
    |.NET Framework\-Laufzeitversion|XML|  
    |-------------------------------------|---------|  
    |4 Client|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0,Profile\=Client" \/\>|  
    |4 Full|\<supportedRuntime version\="v4.0.30319" sku\=".NETFramework,Version\=v4.0" \/\>|  
    |3.5 Full|\<supportedRuntime version\="v2.0.50727"\/\>|  
    |3.5 Client|\<supportedRuntime version\="v2.0.50727" sku\="Client"\/\>|  
  
### So ändern Sie das Anwendungsmanifest, um abhängige Assemblys als .NET Framework\-Assemblys zu kennzeichnen.  
  
1.  Öffnen Sie im Veröffentlichungsverzeichnis das Anwendungsmanifest mit dem XML\-Editor in Visual Studio.  Das Bereitstellungsmanifest hat die Dateinamenerweiterung ".manifest".  
  
2.  Fügen Sie `group="framework"` dem Abhängigkeits\-XML für die Sentinelassemblys \(`System.Core`, `WindowsBase`, `Sentinel.v3.5Client` und `System.Data.Entity`\) hinzu.  Das XML sollte der Darstellung im folgenden Beispiel entsprechen:  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Aktualisieren Sie die Versionsnummer vom `<assemblyIdentity>`\-Element für Microsoft.Windows.CommonLanguageRuntime auf die Versionsnummer für .NET Framework, die der niedrigste allgemeine Nenner ist.  Wenn die Anwendung z. B. auf .NET Framework 3.5 und [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] abzielt, verwenden Sie die Versionsnummer 2.0.50727.0. Das XML sollte wie folgt aussehen:  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### So können Sie die Anwendungs\- und Bereitstellungsmanifeste aktualisieren und erneut signieren  
  
-   Aktualisieren Sie die Anwendungs\- und Bereitstellungsmanifeste, und signieren Sie sie erneut.  Weitere Informationen finden Sie unter [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks\> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [Konfigurationsdateischema](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)