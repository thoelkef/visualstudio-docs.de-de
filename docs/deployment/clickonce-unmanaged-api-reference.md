---
title: ClickOnce-API-Referenz zur nicht verwalteten | Microsoft Docs
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
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 11e10800ff51abd6f95447d85204a44f8367f551
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Referenz zur nicht verwalteten API für ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]nicht verwaltete öffentliche APIs aus dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Löscht oder deinstalliert alle onlineanwendungen aus der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungscache.  
  
### <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, 0 x 80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Hinweise  
 Durch Aufrufen von CleanOnlineAppCache startet die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dienst, wenn er nicht bereits ausgeführt wird.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Ruft Informationen zur Bereitstellung aus dem Manifest und Aktivierung URL ab.  
  
### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|Typ|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Ein Zeiger auf die `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Ein Zeiger auf die `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Ein Zeiger auf einen Puffer um eine NULL-terminierte Zeichenfolge empfangen, die angibt, die Identität des vollständigen zurückgegeben.|LPWSTR|  
|`pdwIdentityBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzApplicationIdentity` Puffers in WCHARs so lang wie. Dies schließt den Platz für das NULL-Zeichen beendet.|LPDWORD|  
|`pwzProcessorArchitecture`|Ein Zeiger auf einen Puffer zur Aufnahme von einer auf NULL endende Zeichenfolge, die die Prozessorarchitektur der anwendungsbereitstellung, aus dem Manifest angibt.|LPWSTR|  
|`pdwArchitectureBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzProcessorArchitecture` Puffers in WCHARs so lang wie.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Ein Zeiger auf einen Puffer zur Aufnahme von einer NULL-terminierte Zeichenfolge, die die Codebasis des Anwendungsmanifests aus dem Manifest angibt.|LPWSTR|  
|`pdwCodebaseBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzApplicationManifestCodebase` Puffers in WCHARs so lang wie.|LPDWORD|  
|`pwzDeploymentProvider`|Ein Zeiger auf einen Puffer zur Aufnahme einer NULL-terminierte Zeichenfolge angibt, die Bereitstellungsanbieter aus dem Manifest, falls vorhanden. Andernfalls wird eine leere Zeichenfolge zurückgegeben.|LPWSTR|  
|`pdwProviderBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Gibt HRESULTFROMWIN32 zurück, wenn ein Puffer zu klein ist.  
  
### <a name="remarks"></a>Hinweise  
 Zeiger darf nicht null sein. `pcwzActivationUrl`und `pcwzPathToDeploymentManifest` darf nicht leer sein.  
  
 Es ist der Verantwortung des Aufrufers, um die Aktivierungs-URL zu bereinigen. Beispielsweise Zeichen Escape hinzufügen, in denen sie benötigt werden, oder entfernen die Abfragezeichenfolge.  
  
 Es ist die Eingabe Länge beschränkt werden in der Verantwortung des Aufrufers. Beispielsweise ist die maximale URL-Länge 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Startet oder eine Anwendung über eine URL für die Bereitstellung installiert.  
  
### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|Typ|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Ein Zeiger auf eine auf NULL endende Zeichenfolge, die die URL des Bereitstellungsmanifests enthält.|LPCWSTR|  
|`data`|Für zukünftige Verwendung reserviert. NULL muss sein.|LPVOID|  
|`flags`|Für zukünftige Verwendung reserviert. 0 muss sein.|DWORD|  
  
### <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, 0 x 80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>