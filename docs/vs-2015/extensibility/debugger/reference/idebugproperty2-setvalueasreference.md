---
title: 'IDebugProperty2:: setvalueasreference | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a94e3767ee05e39e847af27dc5999fa8bbbe2d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193456"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rgpArgs`  
 in Ein Array von Argumenten, die an den Eigenschaften Setter für verwaltete Code übergeben werden. Wenn der Eigenschaften Setter keine Argumente annimmt oder dieses [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt nicht auf einen solchen Eigenschaften Setter verweist, `rgpArgs` sollte ein NULL-Wert sein. Dieser Parameter ist in der Regel ein NULL-Wert.  
  
 `dwArgCount`  
 in Die Anzahl der Argumente im `rgpArgs` Array.  
  
 `pValue`  
 in Ein Verweis in Form eines [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekts auf den Wert, der zum Festlegen dieser Eigenschaft verwendet werden soll.  
  
 `dwTimeout`  
 in Gibt an, wie lange die Festlegung des Werts dauert (in Millisekunden). Ein typischer Wert ist `INFINITE` . Dies wirkt sich auf die Zeitspanne aus, die eine mögliche Auswertung annehmen kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben, in der Regel einer der folgenden:  
  
|Fehler|BESCHREIBUNG|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Das Festlegen des Werts aus einem Verweis wird nicht unterstützt.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, da sich diese Eigenschaft auf eine Methode bezieht.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
