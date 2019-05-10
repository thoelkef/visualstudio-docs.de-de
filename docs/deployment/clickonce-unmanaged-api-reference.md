---
title: Nicht verwalteten für ClickOnce-API-Referenz | Microsoft-Dokumentation
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900272"
---
# <a name="clickonce-unmanaged-api-reference"></a>Referenz zur nicht verwalteten API für ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nicht verwaltete öffentliche APIs aus dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Löscht oder deinstalliert alle online-Anwendungen aus dem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungscache.

### <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, 0 x 80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Hinweise
 Durch Aufrufen von CleanOnlineAppCache startet die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] service, sofern er nicht bereits ausgeführt wird.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Ruft Informationen zur Bereitstellung von der URL-Manifest und Aktivierung ab.

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|Typ|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|Ein Zeiger auf `ActivationURL`.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|Ein Zeiger auf `PathToDeploymentManifest`.|LPCWSTR|
|`pwzApplicationIdentity`|Ein Zeiger auf einen Puffer zur Aufnahme von einer auf NULL endende Zeichenfolge, die angibt, die Identität des vollständigen zurückgegeben.|LPWSTR|
|`pdwIdentityBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzApplicationIdentity` Puffers in WCHARs so lang wie. Dies umfasst den Speicherplatz für das NULL-Abschlusszeichen.|LPDWORD|
|`pwzProcessorArchitecture`|Ein Zeiger auf einen Puffer zur Aufnahme von einer auf NULL endende Zeichenfolge, die die Prozessorarchitektur der anwendungsbereitstellung, aus dem Manifest angibt.|LPWSTR|
|`pdwArchitectureBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzProcessorArchitecture` Puffers in WCHARs so lang wie.|LPDWORD|
|`pwzApplicationManifestCodebase`|Ein Zeiger auf einen Puffer zur Aufnahme von einer auf NULL endende Zeichenfolge, die die Codebasis des Anwendungsmanifests, aus dem Manifest angibt.|LPWSTR|
|`pdwCodebaseBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzApplicationManifestCodebase` Puffers in WCHARs so lang wie.|LPDWORD|
|`pwzDeploymentProvider`|Ein Zeiger auf einen Puffer zur Aufnahme einer NULL-terminierte Zeichenfolge gibt an, dass der Bereitstellungsanbieter "aus dem Manifest vorhanden. Andernfalls wird eine leere Zeichenfolge zurückgegeben.|LPWSTR|
|`pdwProviderBufferLength`|Ein Zeiger auf einen DWORD-Wert, der die Länge der `pwzProviderBufferLength`.|LPDWORD|

### <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Gibt HRESULTFROMWIN32 zurück, wenn ein Puffer zu klein ist.

### <a name="remarks"></a>Hinweise
 Zeiger darf nicht null sein. `pcwzActivationUrl` und `pcwzPathToDeploymentManifest` darf nicht leer sein.

 Es ist der Verantwortung des Aufrufers, um die Aktivierungs-URL zu bereinigen. Beispielsweise Zeichen das Escapezeichen hinzufügen, wo sie benötigt werden, oder entfernen die Abfragezeichenfolge.

 Es ist der Verantwortung des Aufrufers die Eingabe Länge beschränkt. Beispielsweise ist die maximale URL-Länge 2KB.

## <a name="launchapplication"></a>LaunchApplication
 Startet oder eine Anwendung über eine URL für die Bereitstellung installiert.

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|Typ|
|---------------|-----------------|----------|
|`deploymentUrl`|Ein Zeiger auf eine auf NULL endende Zeichenfolge, die die URL des Bereitstellungsmanifests enthält.|LPCWSTR|
|`data`|Für zukünftige Verwendung reserviert. Muss NULL sein.|LPVOID|
|`flags`|Für zukünftige Verwendung reserviert. Muss 0 (null) sein.|DWORD|

### <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. andernfalls gibt ein HRESULT, das den Fehler darstellt. Wenn eine verwaltete Ausnahme auftritt, 0 x 80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Siehe auch
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>