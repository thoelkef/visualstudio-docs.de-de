---
title: 'IDebugBinder3:: getallaliases | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc2075ccc37d280640f7559b1454990ee6684f25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555747"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft eine Liste von Aliasen aus dem Programm ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uRequest`  
 in Die maximale Anzahl von Aliasen, die zurückgegeben werden sollen (gibt die Länge des an übergebenen Arrays an `ppAliases` ).  
  
 `ppAliases`  
 [in, out] Array, das mit Aliasen ausgefüllt werden soll (wenn es sich um einen NULL-Wert handelt und `uRequest` 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, von zurückgegeben `puFetched` ).  
  
 `puFetched`  
 vorgenommen Gibt die Anzahl der abgewonnenen Aliase zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
