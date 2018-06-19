---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcd383130c1af1765014adfa438482543c336ede
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118859"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
VERALTET. DARF NICHT VERWENDET WERDEN. Lädt die Symbole für dieses Modul erneut.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszUrlToSymbols`  
 [in] Der Pfad zu den Symbolspeicher.  
  
 `pbstrDebugMessage`  
 [out] Gibt eine informative Meldung, z. B. eine Status- oder Fehlerinformationen Nachricht, der rechts neben den Namen des Moduls, in dem Fenster "Module" angezeigt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Debugging-Modul sollte stets `E_FAIL`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird nicht mehr unterstützt. Implementieren der [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) Methode stattdessen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)