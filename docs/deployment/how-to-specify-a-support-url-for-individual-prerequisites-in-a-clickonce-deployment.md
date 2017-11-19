---
title: "Vorgehensweise: angeben eine Support-URL für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2335c0279c8e7a23e1b514a8264651e73fedebfc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Gewusst wie: Angeben eines Support-URLs für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung
Ein [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Testen der Bereitstellung können Sie für eine Reihe von erforderlichen Komponenten, die auf dem Clientcomputer verfügbar sein müssen die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung ausgeführt. Dazu gehören die erforderliche Mindestversion von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], die Version des Betriebssystems und alle Assemblys, die im globalen Assemblycache (GAC) vorinstalliert sein müssen. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], jedoch nicht installieren diese erforderlichen Komponenten selbst; Wenn eine erforderliche Komponente nicht gefunden wird, einfach Installation anhält und zeigt ein Dialogfeld, die erläutern, warum Fehler bei der Installation gesucht.  
  
 Es gibt zwei Methoden für die Installation der erforderlichen Komponenten. Sie können sie mit einem Bootstrapper-Anwendung installieren. Alternativ können Sie eine Support-URL für einzelne erforderliche Komponenten angeben, die Benutzern im Dialogfeld angezeigt wird, wenn die erforderliche Komponente nicht gefunden wird. Die Seite, die auf diese URL verweist, kann Links zu Anweisungen zum Installieren der erforderlichen Komponente enthalten. Wenn eine Anwendung keine Support-URL für eine einzelne erforderliche Komponente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zeigt die Support-URL angegeben, die im Bereitstellungsmanifest für die Anwendung als Ganzes, wenn er definiert ist.  
  
 Während [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe und MageUI.exe alle dienen zum Generieren von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungen keines dieser Tools direkt unterstützen eine Support-URL für einzelne erforderliche Komponenten angeben. Dieses Dokument wird beschrieben, wie so ändern Sie Ihre Bereitstellung Anwendungsmanifest und das Bereitstellungsmanifest, dazu gehören support-URLs.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Angeben einer Support-URL für eine einzelne erforderliche Komponente  
  
1.  Öffnen Sie das Anwendungsmanifest (die .manifest-Datei) für Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung in einem Text-Editor.  
  
2.  Für ein erforderliches Betriebssystem hinzufügen der `supportUrl` -Attribut auf die `dependentOS` Element:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Fügen Sie für eine Voraussetzung für eine bestimmte Version der common Language Runtime, die `supportUrl` -Attribut auf die `dependentAssembly` Eintrag, der angibt, die common Language Runtime-Abhängigkeit:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Legen Sie für eine Voraussetzung für eine Assembly, die im globalen Assemblycache vorinstalliert sein muss, die `supportUrl` für die `dependentAssembly` Element, das die erforderliche Assembly angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Dies ist optional. Für Anwendungen, die auf .NET Framework 4 abzielen öffnen Sie das Bereitstellungsmanifest (die .application-Datei) für Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendung in einem Text-Editor.  
  
6.  Erforderliche .NET Framework 4, fügen die `supportUrl` -Attribut auf die `compatibleFrameworks` Element:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Nachdem Sie das Anwendungsmanifest manuell geändert haben, müssen Sie erneut die Anwendungsmanifestdatei mithilfe Ihrer digitale Zertifikat signieren und dann zu aktualisieren und als auch das Bereitstellungsmanifest erneut signieren. Verwenden Sie Mage.exe oder MageUI.exe SDK-tools für diese Aufgabe als Neugenerieren diese Dateien mithilfe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] löscht manuellen Änderungen. Weitere Informationen zur Verwendung von Mage.exe zum Manifest neu signieren finden Sie unter [wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifeste](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Support-URL wird nicht im Dialogfeld angezeigt, wenn die Anwendung für die Ausführung unter teilweiser Vertrauenswürdigkeit gekennzeichnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<CompatibleFrameworks >-Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)