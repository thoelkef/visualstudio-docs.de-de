---
title: 'Vorgehensweise: Angeben einer Support-URL für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679968"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Gewusst wie: Angeben eines Support-URLs für einzelne erforderliche Komponenten in einer ClickOnce-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung kann eine Reihe von Voraussetzungen testen, die auf dem Client Computer verfügbar sein müssen, damit die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung ausgeführt werden kann. Hierzu gehören die erforderliche Mindestversion von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , die Version des Betriebssystems und alle Assemblys, die im globalen Assemblycache (Global Assembly Cache, GAC) vorinstalliert werden müssen. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]kann jedoch keine dieser erforderlichen Komponenten installieren. Wenn eine Voraussetzung nicht gefunden wird, wird die Installation einfach angehalten, und es wird ein Dialogfeld angezeigt, in dem die Gründe für die Installation  
  
 Es gibt zwei Methoden zum Installieren der erforderlichen Komponenten. Sie können Sie mit einer Boots Trapper-Anwendung installieren. Alternativ können Sie eine Support-URL für einzelne erforderliche Komponenten angeben, die Benutzern im Dialogfeld angezeigt wird, wenn die Voraussetzungen nicht gefunden werden. Die Seite, auf die diese URL verweist, kann Links zu Anweisungen für die Installation der erforderlichen Voraussetzungen enthalten. Wenn eine Anwendung keine Unterstützungs-URL für eine einzelne Voraussetzung angibt, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zeigt die im Bereitstellungs Manifest für die Anwendung als Ganzes angegebene Support-URL an, sofern diese definiert ist.  
  
 Obwohl [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Mage.exe und MageUI.exe zum Generieren von bereit Stellungen verwendet werden können [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , unterstützt keines dieser Tools direkt die Angabe einer Support-URL für die einzelnen Voraussetzungen. In diesem Dokument wird beschrieben, wie Sie das Anwendungs Manifest und das Bereitstellungs Manifest für die Bereitstellung so ändern, dass diese unterstützten URLs  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Angeben einer Unterstützungs-URL für eine individuelle Voraussetzung  
  
1. Öffnen Sie das Anwendungs Manifest (die Manifest-Datei) für Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung in einem Text-Editor.  
  
2. Fügen Sie das-Attribut für eine erforderliche Betriebssystem `supportUrl` Komponente dem- `dependentOS` Element hinzu:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Um eine Voraussetzung für eine bestimmte Version des Common Language Runtime zu erhalten, fügen Sie das-Attribut dem-Eintrag hinzu, der `supportUrl` `dependentAssembly` die Common Language Runtime Abhängigkeit angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Um eine Voraussetzung für eine Assembly zu erhalten, die im globalen Assemblycache vorinstalliert werden muss, legen Sie `supportUrl` für das-Element fest, `dependentAssembly` das die erforderliche Assembly angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Optional. Öffnen Sie für Anwendungen, die auf die .NET Framework 4 abzielen, das Bereitstellungs Manifest (die Anwendungsdatei) für Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung in einem Text-Editor.  
  
6. Fügen Sie für eine .NET Framework 4-Voraussetzung das-Attribut dem- `supportUrl` `compatibleFrameworks` Element hinzu:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Nachdem Sie das Anwendungs Manifest manuell geändert haben, müssen Sie das Anwendungs Manifest mit Ihrem digitalen Zertifikat erneut signieren und dann das Bereitstellungs Manifest aktualisieren und erneut signieren. Zum Ausführen dieser Aufgabe müssen Sie die Mage.exe-oder MageUI.exe-SDK-Tools verwenden, wenn Sie diese Dateien mithilfe von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] löscht ihre manuellen Änderungen. Weitere Informationen zum Verwenden von Mage.exe zum erneuten Signieren von Manifesten finden Sie unter Gewusst [wie: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Die Support-URL wird im Dialogfeld nicht angezeigt, wenn die Anwendung für die Ausführung mit teilweiser Vertrauenswürdigkeit markiert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Gewisses](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Erforderliche Anwendungs Bereitstellungs Voraussetzungen](../deployment/application-deployment-prerequisites.md)
