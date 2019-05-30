---
title: Mithilfe von ClickOnce zum Bereitstellen von multitarget apps
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: de3ca40696549ad9208ffd181f8dbc4e7f092b5d
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263204"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>Vorgehensweise: Verwenden von ClickOnce zum Bereitstellen von Anwendungen, die unter mehreren Versionen von .NET Framework ausgeführt werden können
Sie können eine Anwendung bereitstellen, die mehrere Versionen von .NET Framework ausgerichtet ist, mithilfe der ClickOnce-bereitstellungstechnologie. Dies erfordert, dass Sie generieren und aktualisieren die Anwendungs- und Bereitstellungsmanifeste.

> [!NOTE]
> Bevor Sie die Anwendung mehrere Versionen von .NET Framework als Ziel festlegen, sollten Sie sicherstellen, dass Ihre Anwendung mit mehreren Versionen von .NET Framework ausgeführt wird. Die Version der common Language Runtime unterscheidet zwischen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] im Vergleich zu .NET Framework 2.0, .NET Framework 3.0 und .NET Framework 3.5.

 Dieser Prozess erfordert die folgenden Schritte aus:

1. Die Anwendungs- und Bereitstellungsmanifeste zu generieren.

2. Ändern Sie das Bereitstellungsmanifest, um mehrere .NET Framework-Versionen aufzulisten.

3. Ändern der *"App.config"* Datei, die die kompatiblen Versionen von .NET Framework Common Language Runtime-Liste.

4. Ändern Sie das Anwendungsmanifest, um abhängige Assemblys als .NET Framework-Assemblys zu kennzeichnen.

5. Melden Sie das Anwendungsmanifest an.

6. Aktualisieren und das Bereitstellungsmanifest zu signieren.

### <a name="to-generate-the-application-and-deployment-manifests"></a>Um die Anwendungs- und Bereitstellungsmanifeste zu generieren.

- Verwenden Sie den Webpublishing-Assistenten oder die Seite "Veröffentlichen", Projekt-Designer zum Veröffentlichen der Anwendung und generieren die Anwendung und der Bereitstellungsmanifestdateien an. Weitere Informationen finden Sie unter [Vorgehensweise: Veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) oder [Seite "Veröffentlichen", Projekt-Designer](../ide/reference/publish-page-project-designer.md).

### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>So ändern Sie das Bereitstellungsmanifest zum Auflisten der mehrere Versionen von .NET Framework

1. Öffnen Sie im Veröffentlichungsverzeichnis das Bereitstellungsmanifest, indem Sie mit der XML-Editor in Visual Studio. Das Bereitstellungsmanifest hat die *.application* Dateinamenerweiterung.

2. Ersetzen Sie den XML-Code zwischen den `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` und `</compatibleFrameworks>` Elemente mit XML, das die unterstützten Versionen von .NET Framework für Ihre Anwendung enthält.

     Die folgende Tabelle zeigt einige der verfügbaren .NET Framework-Versionen und den entsprechenden XML-Code, der das Bereitstellungsmanifest hinzugefügt werden können.

    |.NET Framework-Version|XML|
    |----------------------------|---------|
    |4 Client|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|
    |4 Full|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|
    |3.5 Client|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|
    |3.5 Full|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|

### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>So ändern Sie die Datei "App.config", um die kompatiblen Versionen von .NET Framework Common Language Runtime-Liste

1. Öffnen Sie im Projektmappen-Explorer die *"App.config"* -Datei mit dem XML-Editor in Visual Studio.

2. Ersetzen Sie den XML-Code zwischen (oder hinzufügen) die `<startup>` und `</startup>` Elemente mit XML, das die unterstützten .NET Framework-Laufzeiten für Ihre Anwendung enthält.

     Die folgende Tabelle zeigt einige der verfügbaren .NET Framework-Versionen und den entsprechenden XML-Code, der das Bereitstellungsmanifest hinzugefügt werden können.

    |.NET Framework Common Language Runtime-version|XML|
    |------------------------------------|---------|
    |4 Client|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|
    |4 Full|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|
    |3.5 Full|\<supportedRuntime version="v2.0.50727"/>|
    |3.5 Client|\<supportedRuntime version="v2.0.50727" sku="Client"/>|

### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>So ändern Sie das Anwendungsmanifest, um abhängige Assemblys als .NET Framework-Assemblys zu kennzeichnen.

1. Öffnen Sie im Veröffentlichungsverzeichnis das Anwendungsmanifest, indem Sie mit der XML-Editor in Visual Studio. Das Bereitstellungsmanifest hat die *". manifest"* Dateinamenerweiterung.

2. Hinzufügen `group="framework"` der Abhängigkeits-XML für die Sentinelassemblys (`System.Core`, `WindowsBase`, `Sentinel.v3.5Client`, und `System.Data.Entity`). Der XML-Code sollte beispielsweise wie folgt aussehen:

   ```xml
   <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">
   ```

3. Aktualisieren Sie die Versionsnummer der `<assemblyIdentity>` -Element für Microsoft.Windows.CommonLanguageRuntime der Versionsnummer für das .NET Framework, das den kleinsten gemeinsamen Nenner ist. Angenommen, die Anwendung .NET Framework 3.5 abzielt und [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)], verwenden die 2.0.50727.0-Versionsnummer und den XML-Code sollte wie folgt aussehen:

   ```xml
   <dependency>
     <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
       <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />
     </dependentAssembly>
   </dependency>
   ```

### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>Zum Aktualisieren und erneut signieren, die Anwendungs- und Bereitstellungsmanifeste

- Aktualisieren und erneut die Anwendungs- und Bereitstellungsmanifeste zu signieren. Weitere Informationen finden Sie unter [Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Siehe auch
- [Publish ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md)
- [\<CompatibleFrameworks >-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [\<Dependency >-Element](../deployment/dependency-element-clickonce-application.md)
- [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
- [Konfigurationsdateischema](/dotnet/framework/configure-apps/file-schema/index)
