---
title: 'IDebugProcess3:: Continue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 92a36bb7e89d8afaa6d76f7d7b3772bd1714ffa7
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386237"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Setzt die Ausführung dieses Prozesses mit dem Status "beendet" fort. Alle vorherigen Ausführungs Zustände (z. b. ein Schritt) werden beibehalten, und der Prozess wird erneut ausgeführt.  
  
> [!NOTE]
> Diese Methode sollte anstelle von [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)verwendet werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pThread`  
 in Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den fort zufügenden Thread darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird für diesen Prozess aufgerufen, unabhängig davon, wie viele Prozesse gedebuggt werden oder welcher Prozess das anhalteereignis generiert hat. Die Implementierung muss den vorherigen Ausführungs Zustand beibehalten (z. b. einen Schritt) und die Ausführung fortsetzen, als ob Sie vor dem Abschließen der vorherigen Ausführung nie beendet worden wäre. Das heißt, wenn ein Thread in diesem Prozess einen Schritt-für-Vorgang ausgeführt hat und beendet wurde, weil ein anderer Prozess angehalten wurde, und dann `Continue` aufgerufen wurde, muss der angegebene Thread den ursprünglichen Step-over-Vorgang beenden.  
  
 **Warnung** Senden Sie während der Behandlung dieses Aufrufes kein anhalteereignis oder ein sofortiges (synchrones [) Ereignis.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Andernfalls reagiert der Debugger möglicherweise nicht mehr.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
