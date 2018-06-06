---
title: 'Vorgehensweise: Verwenden Sie ClickOnce zum Bereitstellen von Anwendungen, die auf mehrere Versionen von .NET Framework ausgeführt werden kann | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 0ea5606913a4afb082fda09644dad7af8031a7e2
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815073"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Gewusst wie: Verwenden von ClickOnce zum Bereitstellen von Anwendungen, die unter mehreren Versionen von .NET Framework ausgeführt werden können
Sie können eine Anwendung bereitstellen, die auf mehrere Versionen von .NET Framework abzielen, mithilfe von ClickOnce-Technologie. Dies erfordert, dass Sie generieren und aktualisieren die Anwendungs- und Bereitstellungsmanifeste.  
  
> [!NOTE]
>  Bevor Sie die Anwendung auf mehrere Versionen von .NET Framework als Ziel ändern, sollten Sie sicherstellen, dass Ihre Anwendung mit mehreren Versionen von .NET Framework ausgeführt wird. Die Version der common Language Runtime unterscheidet sich zwischen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] im Vergleich zu .NET Framework 2.0, .NET Framework 3.0 und .NET Framework 3.5.  
  
 Dieser Prozess erfordert die folgenden Schritte aus:  
  
1.  Generieren Sie die Anwendungs- und Bereitstellungsmanifeste.  
  
2.  Ändern Sie das Bereitstellungsmanifest, um mehrere .NET Framework-Versionen aufzulisten.  
  
3.  Ändern Sie die Datei "App.config", um die kompatiblen Versionen von .NET Framework Common Language Runtime aufzulisten.  
  
4.  Ändern Sie das Anwendungsmanifest, um abhängige Assemblys als .NET Framework-Assemblys zu kennzeichnen.  
  
5.  Melden des Anwendungsmanifests.  
  
6.  Aktualisieren Sie und signieren Sie des Bereitstellungsmanifests.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>Um die Anwendungs- und Bereitstellungsmanifeste zu generieren.  
  
-   Verwenden Sie den Veröffentlichungs-Assistenten oder die Seite "Veröffentlichen" im Projekt-Designer zum Veröffentlichen der Anwendung und generieren die Anwendung und die Bereitstellungsmanifestdateien an. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) oder [Seite "Veröffentlichen", Projekt-Designer](../ide/reference/publish-page-project-designer.md).  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>So ändern Sie das Bereitstellungsmanifest, um die Liste mehrere .NET Framework-Versionen  
  
1.  Öffnen Sie das Bereitstellungsmanifest mithilfe der XML-Editor in Visual Studio, in das Veröffentlichungsverzeichnis. Das Bereitstellungsmanifest hat die Erweiterung .application.  
  
2.  Ersetzen Sie den XML-Code zwischen den `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` und `</compatibleFrameworks>` Elemente mit XML, die die unterstützten Versionen von .NET Framework für Ihre Anwendung aufgeführt.  
  
     Die folgende Tabelle zeigt einige der verfügbaren .NET Framework-Versionen und das entsprechende XML, die Sie auf das Bereitstellungsmanifest hinzufügen können.  
  
    |.NET Framework-Version|XML|  
    |----------------------------|---------|  
    |4-client|\<Framework TargetVersion = "4.0" Profile = "Client" SupportedRuntime = "4.0.30319" / >|  
    |4 full|\<Framework TargetVersion = "4.0" Profil "Full" SupportedRuntime = = "4.0.30319" / >|  
    |3.5-client|\<Framework TargetVersion = "3.5" Profile = "Client" SupportedRuntime = "2.0.50727" / >|  
    |3.5 vollständige|\<Framework TargetVersion = "3.5" Profil "Full" SupportedRuntime = = "2.0.50727" / >|  
    |3.0|\<Framework TargetVersion = "3.0" SupportedRuntime = "2.0.50727" / >|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>So ändern Sie die Datei "App.config", um die kompatiblen Versionen von .NET Framework Common Language Runtime aufzulisten  
  
1.  Öffnen Sie im Projektmappen-Explorer die Datei "App.config" mithilfe der XML-Editor in Visual Studio.  
  
2.  Ersetzen Sie (oder hinzufügen) den XML-Code zwischen den `<startup>` und `</startup>` Elemente mit XML, die die unterstützten .NET Framework-Laufzeiten für Ihre Anwendung aufgeführt.  
  
     Die folgende Tabelle zeigt einige der verfügbaren .NET Framework-Versionen und das entsprechende XML, die Sie auf das Bereitstellungsmanifest hinzufügen können.  
  
    |.NET Framework Common Language Runtime-version|XML|  
    |------------------------------------|---------|  
    |4-client|\<SupportedRuntime-Version = "v4.0.30319" Sku = ". NETFramework, Version = v4. 0, Profile = Client "/ >|  
    |4 full|\<SupportedRuntime-Version = "v4.0.30319" Sku = ". NETFramework, Version = v4. 0 "/ >|  
    |3.5 vollständige|\<SupportedRuntime version="v2.0.50727"/ >|  
    |3.5-client|\<SupportedRuntime-Version = "v2.0.50727" Sku = "Client" / >|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>So ändern Sie das Anwendungsmanifest, um abhängige Assemblys als .NET Framework-Assemblys zu kennzeichnen.  
  
1.  Öffnen Sie das Anwendungsmanifest im Veröffentlichungsverzeichnis mithilfe der XML-Editor in Visual Studio. Das Bereitstellungsmanifest hat die Erweiterung. manifest.  
  
2.  Hinzufügen `group="framework"` die Abhängigkeits-XML für die Sentinelassemblys (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, und `System.Data.Entity`). Der XML-Code sollte beispielsweise wie folgt aussehen:  
  
    ```xml  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3.  Aktualisieren Sie die Versionsnummer der `<assemblyIdentity>` -Element für Microsoft.Windows.CommonLanguageRuntime auf die Versionsnummer für .NET Framework, das die niedrigste (Standard) gemeinsamen Nenner ist. Angenommen, wenn die Anwendung .NET Framework 3.5 abzielt und [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], verwenden die 2.0.50727.0-Versionsnummer und den XML-Code sollte wie folgt aussehen:  
  
    ```xml  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Zum Aktualisieren und erneut signieren die Anwendungs- und Bereitstellungsmanifeste  
  
-   Aktualisieren Sie und signieren Sie die Anwendungs- und Bereitstellungsmanifeste erneut. Weitere Informationen finden Sie unter [Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [\<CompatibleFrameworks >-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<Dependency >-Element](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [Konfigurationsdateischema](/dotnet/framework/configure-apps/file-schema/index)