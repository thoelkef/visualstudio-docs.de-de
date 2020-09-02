---
title: 'Ienumentbugfields:: Reset | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62a9039a1fa9b53c57f9eb61047f0b870835d5ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199616"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode setzt die Enumeration auf das erste Element zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf von [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) das erste Element der-Enumeration zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Nächste](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
