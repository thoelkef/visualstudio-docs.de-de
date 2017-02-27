---
title: "&lt;entryPoint&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#commandLine"
  - "urn:schemas-microsoft-com:asm.v2#entryPoint"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<entryPoint> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], entryPoint element"
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;entryPoint&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die Assembly, die ausgeführt werden muss, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung auf einem Clientcomputer ausgeführt wird.  
  
## Syntax  
  
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
  
## Elemente und Attribute  
 Das `entryPoint`\-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v2`\-Namespace.  Es gibt möglicherweise nur ein in einem Anwendungsmanifest definiertes `entryPoint`\-Element.  
  
 Das `entryPoint`\-Element verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Optional.  Dieser Wert wird nicht von .NET Framework verwendet.|  
  
 `entryPoint` weist folgende Elemente auf.  
  
## assemblyIdentity  
 Erforderlich.  Die Rolle von `assemblyIdentity` und die zugehörigen Attribute werden unter [\<assemblyIdentity\> Element](../deployment/assemblyidentity-element-clickonce-application.md) definiert.  
  
 Das `processorArchitecture`\-Attribut dieses Elements und das `processorArchitecture`\-Attribut, das in `assemblyIdentity` an einer anderen Stelle im Anwendungsmanifest definiert ist, müssen sich entsprechen.  
  
## commandLine  
 Erforderlich.  Muss ein untergeordnetes Element des `entryPoint`\-Elements sein.  Es weist keine untergeordneten Elemente auf und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`file`|Erforderlich.  Ein lokaler Verweis auf die Startassembly für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  Dieser Wert kann nicht die folgenden Pfadtrennzeichen enthalten: Schrägstrich \(\/\) oder umgekehrter Schrägstrich \(\\\).|  
|`parameters`|Erforderlich.  Beschreibt die Aktion, die bei dem Einstiegspunkt ausgeführt werden soll.  Der einzige gültige Wert lautet `run`. Wenn eine leere Zeichenfolge angegeben wird, wird der Wert `run` angenommen.|  
  
## customHostRequired  
 Optional.  Wenn vorhanden gibt es an, dass die Bereitstellung keine eigenständige Anwendung ist, sondern eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt wird.  
  
 Wenn dieses Element vorhanden ist, dürfen die Elemente `assemblyIdentity` und `commandLine` nicht ebenfalls vorhanden sein.  Wenn sie vorhanden sind, löst [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] während der Installation einen Validierungsfehler aus.  
  
 Dieses Element verfügt über keine Attribute und keine untergeordneten Elemente.  
  
## customUX  
 Optional.  Gibt an, dass die Anwendung von einem benutzerdefinierten Installationsprogramm installiert und verwaltet wird, und erstellt keinen Eintrag im Startmenü, eine Verknüpfung oder einen Eintrag in "Software".  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Eine Anwendung, die das customUX\-Element einschließt, muss ein benutzerdefiniertes Installationsprogramm bereitstellen, das die <xref:System.Deployment.Application.InPlaceHostingManager>\-Klasse verwendet, um Installationsvorgänge auszuführen.  Eine Anwendung mit diesem Element kann nicht installiert werden, indem man auf das Manifest oder den erforderlichen setup.exe\-Bootstrapper doppelklickt.  Das benutzerdefinierte Installationsprogramm kann Startmenüeinträge, Verknüpfungen und Einträge aus "Software" erstellen.  Wenn das benutzerdefinierte Installationsprogramm keinen Eintrag in "Software" erstellt, muss der von der <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A>\-Eigenschaft bereitgestellte Abonnementbezeichner gespeichert werden, und der Benutzer muss die Anwendung später durch Aufrufen der <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A>\-Methode deinstallieren können.  Weitere Informationen finden Sie unter [Walkthrough: Creating a Custom Installer for a ClickOnce Application](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## Hinweise  
 Dieses Element identifiziert die Assembly und den Einstiegspunkt für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung.  
  
 `commandLine` kann nicht verwendet werden, um zur Laufzeit Parameter an die Anwendung zu übergeben.  Sie können über die <xref:System.AppDomain> der Anwendung auf Abfragezeichenfolgen\-Parameter für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung zugreifen.  Weitere Informationen finden Sie unter [Gewusst wie: Abrufen von Abfragezeichenfolgen\-Informationen in einer Online\-ClickOnce\-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `entryPoint`\-Element in einem Anwendungsmanifest für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreichen Beispiels, das für das Thema [ClickOnce\-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) bereitgestellt wird.  
  
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
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)