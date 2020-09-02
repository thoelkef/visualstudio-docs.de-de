---
title: 'Ienumentbugcustomattribute:: Reset | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ff86808bfd33cf7112091b028140f538932dee28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551350"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Setzt die Enumerationsfolge auf den Anfang zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) -Methode das erste Element der-Enumeration zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ienumentbugcustomattribute](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Nächste](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
