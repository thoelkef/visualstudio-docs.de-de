---
title: 'IDebugPort2:: getportname | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortName
helpviewer_keywords:
- IDebugPort2::GetPortName
ms.assetid: 4478b3d5-aa30-4105-8d05-e3bae2f8917a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25952355f77acb30587b7aab9820dfc1bed36507
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202900"
---
# <a name="idebugport2getportname"></a>IDebugPort2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Portnamen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 vorgenommen Gibt den Namen des Ports zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
