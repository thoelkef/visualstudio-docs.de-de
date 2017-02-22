---
title: "ClickOnce Unmanaged API Reference | Microsoft Docs"
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
  - "LaunchApplication [ClickOnce unmanaged]"
  - "ClickOnce, unmanaged APIs"
  - "CleanOnlineAppCache [ClickOnce unmanaged]"
  - "CleanOnlineAppCacheW interface [ClickOnce unmanaged]"
  - "GetDeploymentDataFromManifest [ClickOnce unmanaged]"
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Unmanaged API Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht verwaltete öffentliche APIs aus dfshim.dll.  
  
## CleanOnlineAppCache  
 Reinigt oder deinstalliert alle Onlineanwendungen aus dem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungscache.  
  
### Rückgabewert  
 Gibt bei Erfolg S\_OK zurück. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt.  Wenn eine verwaltete Ausnahme auftritt, wird 0x80020009 \(DISP\_E\_EXCEPTION\) zurückgegeben.  
  
### Hinweise  
 Durch Aufrufen von CleanOnlineAppCache wird der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Dienst gestartet, wenn er nicht bereits ausgeführt wird.  
  
## GetDeploymentDataFromManifest  
 Ruft Bereitstellungsinformationen aus dem Manifest und die Aktivierungs\-URL ab.  
  
### Parameter  
  
|Parameter|Beschreibung|Typ|  
|---------------|------------------|---------|  
|`pcwzActivationUrl`|Ein Zeiger auf `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Ein Zeiger auf `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Ein Zeiger auf einen Puffer zum Empfangen einer auf NULL endenden Zeichenfolge, die die vollständige zurückgegebene Anwendungsidentität angibt.|LPWSTR|  
|`pdwIdentityBufferLength`|Ein Zeiger auf ein DWORD, das in WCHARs so lang wie der `pwzApplicationIdentity`\-Puffer ist.  Dies schließt den Platz für das NULL\-Terminierungszeichen ein.|LPDWORD|  
|`pwzProcessorArchitecture`|Ein Zeiger auf einen Puffer zum Empfangen einer auf NULL endenden Zeichenfolge, die die Prozessarchitektur der Anwendungsbereitstellung aus dem Manifest angibt.|LPWSTR|  
|`pdwArchitectureBufferLength`|Ein Zeiger auf ein DWORD, das in WCHARs so lang wie der `pwzProcessorArchitecture`\-Puffer ist.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Ein Zeiger auf einen Puffer zum Empfangen einer auf NULL endenden Zeichenfolge, die die Codebasis des Anwendungsmanifests aus dem Manifest angibt.|LPWSTR|  
|`pdwCodebaseBufferLength`|Ein Zeiger auf ein DWORD, das in WCHARs so lang wie der `pwzApplicationManifestCodebase`\-Puffer ist.|LPDWORD|  
|`pwzDeploymentProvider`|Ein Zeiger auf einen Puffer zum Empfangen einer auf NULL endenden Zeichenfolge, die den Bereitstellungsanbieter aus dem Manifest angibt, falls vorhanden.  Andernfalls wird eine leere Zeichenfolge zurückgegeben.|LPWSTR|  
|`pdwProviderBufferLength`|Ein Zeiger auf ein DWORD, das so lang wie `pwzProviderBufferLength` ist.|LPDWORD|  
  
### Rückgabewert  
 Gibt bei Erfolg S\_OK zurück. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt.  Gibt HRESULTFROMWIN32 \(ERROR\_INSUFFICIENT\_BUFFER\) zurück, wenn ein Puffer zu klein ist.  
  
### Hinweise  
 Zeiger dürfen nicht NULL sein.  `pcwzActivationUrl` und `pcwzPathToDeploymentManifest` darf nicht leer sein.  
  
 Der Aufrufer ist dafür verantwortlich, die Aktivierungs\-URL zu bereinigen.  Dazu gehören beispielsweise das Hinzufügend von erforderlichen Escapezeichen oder das Entfernen der Abfragezeichenfolge.  
  
 Der Aufrufer ist dafür verantwortlich, die Eingabelänge einzuschränken.  Die maximale URL\-Länge ist beispielsweise 2 KB.  
  
## LaunchApplication  
 Startet oder installiert eine Anwendung mithilfe einer Bereitstellungs\-URL.  
  
### Parameter  
  
|Parameter|Beschreibung|Typ|  
|---------------|------------------|---------|  
|`deploymentUrl`|Ein Zeiger auf eine auf NULL endende Zeichenfolge, die die URL des Bereitstellungsmanifests enthält.|LPCWSTR|  
|`data`|Für zukünftige Verwendung reserviert.  Muss NULL sein.|LPVOID|  
|`flags`|Für zukünftige Verwendung reserviert.  Muss 0 \(null\) sein.|DWORD|  
  
### Rückgabewert  
 Gibt bei Erfolg S\_OK zurück. Andernfalls wird ein HRESULT zurückgegeben, das den Fehler darstellt.  Wenn eine verwaltete Ausnahme auftritt, wird 0x80020009 \(DISP\_E\_EXCEPTION\) zurückgegeben.  
  
## Siehe auch  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>