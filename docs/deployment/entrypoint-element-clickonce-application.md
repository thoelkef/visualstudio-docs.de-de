---
title: '&lt;EntryPoint&gt; Element (ClickOnce-Anwendung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: cd263d8137b380519477d16079e8ed8b1547fbbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;EntryPoint&gt; Element (ClickOnce-Anwendung)
Identifiziert die Assembly, die sollten ausgeführt wird, wenn dies [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung auf einem Clientcomputer ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `entryPoint`-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2`-Namespace. Es kann nur möglich `entryPoint` Element in einem Anwendungsmanifest definiert.  
  
 Die `entryPoint` Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Dies ist optional. Dieser Wert wird von .NET Framework nicht verwendet.|  
  
 `entryPoint` hat die folgenden Elemente:  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Erforderlich. Die Rolle des `assemblyIdentity` und ihre Attribute in [ \<AssemblyIdentity >-Element](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Die `processorArchitecture` Attribut dieses Elements und der `processorArchitecture` -Attribut definiert, der `assemblyIdentity` an anderer Stelle in der Anwendung Manifest muss übereinstimmen.  
  
## <a name="commandline"></a>Befehlszeile  
 Erforderlich. Muss ein untergeordnetes Element von der `entryPoint` Element. Er verfügt über keine untergeordneten Elemente und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`file`|Erforderlich. Einen lokalen Verweis auf die Startassembly für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieser Wert darf keine Schrägstrich (/) oder umgekehrten Schrägstrich enthalten (\\) Pfadtrennzeichen.|  
|`parameters`|Erforderlich. Beschreibt die Aktion an, mit dem Einstiegspunkt an. Der einzige gültige Wert ist `run`; Wenn eine leere Zeichenfolge angegeben wird, `run` wird angenommen.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 Dies ist optional. Wenn enthalten, gibt an, dass diese Bereitstellung eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt werden, und keine eigenständige Anwendung.  
  
 Wenn dieses Element vorhanden ist, wird die `assemblyIdentity` und `commandLine` Elemente dürfen nicht auch vorhanden sein. Wenn dies der Fall, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] löst einen Validierungsfehler während der Installation.  
  
 Dieses Element verfügt über keine Attribute und keine untergeordneten Elemente.  
  
## <a name="customux"></a>customUX  
 Dies ist optional. Gibt an, dass die Anwendung installiert ist und durch ein benutzerdefiniertes Installationsprogramm beibehalten und einen Start Menüeintrag, die Verknüpfung oder das Hinzufügen erstellt oder keine Programme Eintrag zu entfernen.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Eine Anwendung, die das CustomUX-Element enthält muss einem benutzerdefinierten Installationsprogramm, verwendet Bereitstellen der <xref:System.Deployment.Application.InPlaceHostingManager> -Klasse, Vorgänge zu installieren. Eine Anwendung mit diesem Element kann nicht durch Doppelklicken auf die erforderliche Manifest oder eine setup.exe-Bootstrapper installiert werden. Benutzerdefinierte Installer kann Menüeinträge im Start, Verknüpfungen und Software -Einträge erstellen. Wenn benutzerdefinierte Installationsprogramm keinen Software -Eintrag erstellt wird, müssen sie den Abonnementbezeichner gebotenen speichern die <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> -Eigenschaft und der Benutzer später deinstallieren die Anwendung durch Aufrufen der <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> Methode. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen ein benutzerdefiniertes Installationsprogramm für eine ClickOnce-Anwendung](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element identifiziert die Assembly und den Einstiegspunkt für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
 Sie können keine `commandLine` zum Übergeben von Parametern in der Anwendung zur Laufzeit. Sie erreichen die Abfragezeichenfolgen-Parameter für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung aus der Anwendungsverzeichnis <xref:System.AppDomain>. Weitere Informationen finden Sie unter [Vorgehensweise: Abrufen von Abfragezeichenfolgen-Informationen in einer Online-ClickOnce-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht eine `entryPoint` Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) Thema.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)