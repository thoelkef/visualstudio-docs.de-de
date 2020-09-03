---
title: 'Idebugarrayfield:: GetRank | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198729"
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
 vorgenommen Gibt den Rang zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Rang eines Arrays entspricht der Anzahl von Dimensionen. In C++ und c# sind mehrdimensionale Arrays tatsächlich Arrays von Arrays und können daher nur als eindimensionales Array betrachtet werden (und die `GetRank` Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] werden mehrdimensionale Arrays unterschiedlich behandelt, und der Rang eines solchen Arrays spiegelt die Anzahl der Dimensionen wider (und die- `GetRank` Methode gibt immer die Anzahl der Dimensionen zurück).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
