---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53dfbc71239eacba447a36cf95430e5c5da461a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214421"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

VERALTET. VERWENDEN SIE NICHT. Lädt die Symbole für dieses Modul erneut.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

