---
title: IDebugProcess3::D isableumc | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0db9eb44b8074a5c5e3b35a5a5dadcf04f37fb2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841033"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode deaktiviert die Bearbeitung und Fortsetzung für diesen Prozess (und alle darin enthaltenen Programme) explizit. Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `reason`  
 in Ein Wert [aus der](../../../extensibility/debugger/reference/encunavailablereason.md) Enumeration "Enumeration" in "Enumeration".  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.  
  
> [!NOTE]
> Ein benutzerdefinierter Port Lieferant sollte immer zurückgeben `E_NOTIMPL` .  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn "Bearbeiten und Fortfahren" für einen Prozess deaktiviert ist, kann es nur wieder aktiviert werden, indem der Prozess neu gestartet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
