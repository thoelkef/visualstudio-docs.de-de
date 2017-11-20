---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords: IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2499fb1cca7dcbbf278d00c0aac205774d3cb75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Diese Methode ordnet einen Dokumentenkontext, in ein Array von Adressen Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pDocContext`  
 [in] Der Dokumentenkontext.  
  
 `fStatmentOnly`  
 [in] Bei "true", schränkt die Debug-Adressen zu einer einzigen Anweisung.  
  
 `ppEnumBegAddresses`  
 [out] Gibt einen Enumerator für die Debug-Startadressen dieser Anweisung oder der Zeile zugeordnet.  
  
 `ppEnumEndAddresses`  
 [out] Gibt eine [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) Enumerator für die Endadresse Debug-Adressen dieser Anweisung oder der Zeile zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Dokumentenkontext gibt normalerweise an einen Bereich von Quellzeilen. Diese Methode stellt die Start- und endadressen Debug #kommentare zugeordnet. Einige Sprachen ermöglichen Anweisungen, die erstrecken sich über mehrere Zeilen oder Zeilen, die mehr als eine Anweisung enthält. Diese Methode bietet ein Flag, um der Debug-Adressen zu einer einzigen Anweisung zu beschränken.  
  
 Es ist möglich, dass eine einzelne Anweisung mehrere Debug-Adressen, wie im Fall von Vorlagen haben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)