---
title: 'IDebugEngine2:: setmetric | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3371925894a32bfe954979d1554d96d3d5bbb140
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182241"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode legt einen Registrierungs Wert fest, der als Metrik bezeichnet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszMetric`  
 in Der Name der Metrik.  
  
 `varValue`  
 in Gibt den Metrikwert an.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Metrik ist ein Registrierungs Wert, mit dem das Verhalten einer Debug-Engine geändert oder unterstützte Funktionen angekündigt werden. Diese Methode kann den-Befehl an die entsprechende Form der SDK-Hilfsprogramme [für die Debugfunktion](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) weiterleiten `SetMetric` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
