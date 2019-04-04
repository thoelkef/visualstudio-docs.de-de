---
title: IDebugArrayField::GetRank | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960470"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwRank`  
 [out] Gibt den Rang zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Rang eines Arrays entspricht die Anzahl der Dimensionen ab. In C++ und c#, mehrdimensionale Arrays sind wirklich Arrays von Arrays und kann daher nur ein eindimensionales Array betrachtet werden (und die `GetRank` Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], dagegen auf mehrdimensionale Arrays werden anders verarbeitet, und der Rang eines solchen Arrays gibt die Anzahl der Dimensionen (und die `GetRank` Methode wird immer die Anzahl der Dimensionen).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
