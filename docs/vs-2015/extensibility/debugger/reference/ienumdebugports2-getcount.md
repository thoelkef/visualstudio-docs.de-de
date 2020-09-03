---
title: 'IEnumDebugPorts2:: GetCount | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46b000ffefcd8b2277b87cbda3b5c5fafba0a1c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180440"
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Anzahl der Elemente in der-Enumeration zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 vorgenommen Gibt die Anzahl der Elemente in der-Enumeration zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist nicht Teil der üblichen com-Enumerationsschnittstelle, die angibt, dass nur die `Next` `Clone` Methoden,, `Skip` und `Reset` implementiert werden müssen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
