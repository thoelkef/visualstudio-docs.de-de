---
title: 'IDebugBinder3:: geteeservice | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 982802d1e89434322aba4f5078ceb6dd5a850034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193035"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode gibt einen angeforderten Dienst zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `vendor`  
 [in] `GUID` eines Anbieters (ein NULL-Wert ist akzeptabel).  
  
 `language`  
 [in] `GUID` einer Sprache (ein NULL-Wert ist zulässig).  
  
 `iid`  
 [in] `IID` des abzurufenden Dienstanbieter.  
  
 `ppService`  
 vorgenommen Eine Schnittstelle zum angeforderten Dienst.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Übergeben Sie das-Objekt `IID` für die [ieevisualizerserviceprovider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) -Schnittstelle ( `IID_IEEVisualizerServiceProvider` ), um zu überprüfen, ob der Dienst für die typschnell Ansicht verfügbar ist Wenn dies der Fall ist, kann die Ausdrucks Auswertung die [ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md) -Schnittstelle abrufen, um typvisualisierungen zu unterstützen. Weitere Informationen finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [Ieevisualizerserviceprovider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Ieevisualizerservice](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
