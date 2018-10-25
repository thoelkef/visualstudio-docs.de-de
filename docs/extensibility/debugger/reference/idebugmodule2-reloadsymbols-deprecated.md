---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft-Dokumentation
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
ms.openlocfilehash: 09f2e81699683ec49155faceb375da3d636ed4c4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934040"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
VERALTET. VERWENDEN SIE NICHT. Lädt die Symbole für dieses Modul erneut.  
  
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
 [out] Gibt eine informationsmeldung, z. B. eine Status- oder Fehlerinformationen Nachricht, die rechts neben den Namen des Moduls in das Fenster "Module" angezeigt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Eine Debug-Engine sollte immer zurückgeben `E_FAIL`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird nicht mehr unterstützt. Implementieren der [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) Methode stattdessen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)