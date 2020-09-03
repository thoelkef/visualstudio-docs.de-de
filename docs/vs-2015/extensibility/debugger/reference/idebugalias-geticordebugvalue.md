---
title: 'Idebugalias:: geticorentbugvalue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67ab8a7343cd320470515b757dfca905a0a4690e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156276"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine verwaltete Code Schnittstelle ab, die den diesem Alias zugeordneten Wert darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppUnk`  
 [out] `IUnknown` eine Schnittstelle, die den diesem Alias zugeordneten Wert darstellt. Diese Schnittstelle kann für die-Schnittstelle abgefragt werden `ICorDebugValue` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode gilt nur für verwaltete Werte ( `ICorDebugValue` ist eine im verfügbare Schnittstelle, die im [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK in der Datei "Cordebug. idl" definiert ist).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
