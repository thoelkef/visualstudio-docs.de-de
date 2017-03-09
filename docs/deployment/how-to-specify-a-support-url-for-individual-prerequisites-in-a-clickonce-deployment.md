---
title: "How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment | Microsoft Docs"
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
  - "ClickOnce deployment, prerequisites"
  - "ClickOnce deployment, URLs"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung kann überprüfen, ob bestimmte erforderliche Komponenten vorhanden sind, die auf dem Clientcomputer verfügbar sein müssen, damit die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung ausgeführt werden kann.  Dazu gehören die erforderliche Mindestversion von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], die Version des Betriebssystems und alle Assemblys, die im globalen Assemblycache \(GAC\) vorinstalliert sein müssen.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann diese erforderlichen Komponenten jedoch nicht selbst installieren. Falls eine erforderliche Komponente nicht gefunden wird, wird die Installation einfach angehalten, und in einem angezeigten Dialogfeld wird erläutert, warum ein Fehler aufgetreten ist.  
  
 Es gibt zwei Methoden für die Installation von erforderlichen Komponenten.  Sie können diese Komponenten mithilfe einer Bootstrapperanwendung installieren.  Alternativ können Sie eine Support\-URL für einzelne erforderliche Komponenten angeben. Er wird für die Benutzer in einem Dialogfeld angezeigt, wenn die erforderliche Komponente nicht gefunden wird.  Die Seite, auf die von dieser URL verwiesen wird, kann Links zu Anweisungen für die Installation der erforderlichen Komponente enthalten.  Wenn eine Anwendung für eine einzelne erforderliche Komponente keine Support\-URL angibt, zeigt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] die Support\-URL an, die im Bereitstellungsmanifest für die gesamte Anwendung angegeben ist \(sofern definiert\).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe und MageUI.exe können zwar alle zum Generieren von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungen verwendet werden, aber keines dieser Tools unterstützt unmittelbar die Angabe einer Support\-URL für einzelne erforderliche Komponenten.  In diesem Dokument wird beschrieben, wie Sie das Anwendungsmanifest und das Bereitstellungsmanifest der Bereitstellung ändern, um diese Support\-URLs aufzunehmen.  
  
### Angeben einer Support\-URL für eine einzelne erforderliche Komponente  
  
1.  Öffnen Sie in einem Text\-Editor das Anwendungsmanifest \(die MANIFEST\-Datei\) für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
2.  Fügen Sie für ein erforderliches Betriebssystem das `supportUrl`\-Attribut dem `dependentOS`\-Element hinzu:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Fügen Sie für eine bestimmte erforderliche Common Language Runtime\-Version das `supportUrl`\-Attribut dem `dependentAssembly`\-Eintrag hinzu, der die Common Language Runtime\-Abhängigkeit angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Für eine erforderliche Assembly, die im globalen Assemblycache vorinstalliert sein muss, legen Sie den `supportUrl` für das `dependentAssembly`\-Element fest, dass die erforderliche Assembly angibt:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Optional.  Öffnen Sie für Anwendungen, die auf .NET Framework 4 ausgerichtet sind, in einem Text\-Editor das Bereitstellungsmanifest \(die APPLICATION\-Datei\) für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
6.  Fügen Sie für eine erforderliche .NET Framework 4\-Komponente dem `compatibleFrameworks`\-Element das `supportUrl`\-Attribut hinzu:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Nachdem Sie das Anwendungsmanifest manuell geändert haben, müssen Sie es mit Ihrem digitalen Zertifikat neu signieren und anschließend das Bereitstellungsmanifest ebenfalls aktualisieren und neu signieren.  Sie müssen hierfür die SDK\-Tools "Mage.exe" oder "MageUI.exe" verwenden, da Ihre manuell durchgeführten Änderungen bei der Neugenerierung dieser Dateien mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rückgängig gemacht werden.  Weitere Informationen über die Verwendung von Mage.exe zum erneuten Signieren von Manifesten finden Sie unter [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## .NET Framework-Sicherheit  
 Die Support\-URL wird nicht im Dialogfeld angezeigt, wenn die Anwendung für die Ausführung mit teilweiser Vertrauenswürdigkeit gekennzeichnet ist.  
  
## Siehe auch  
 [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> Element](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Vorbedingungen für die Anwendungsbereitstellung](../deployment/application-deployment-prerequisites.md)