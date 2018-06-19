---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 86682bb64f041cd8ee1b08bbec02c28492cac7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107646"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Gibt die ID für den Standort einen Code für einen bestimmten Code-Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCodeContext`  
 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt in einen Bezeichner konvertiert werden.  
  
 `puCodeLocationId`  
 [out] Gibt den Bezeichner der Code-Speicherort. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_CODE_CONTEXT_OUT_OF_SCOPE` , wenn der Codekontext gültig ist, aber außerhalb des Bereichs.  
  
## <a name="remarks"></a>Hinweise  
 Die ID für den Standort Code bezieht sich auf die Debugging-Modul (DE) unterstützen die Disassembly. Diese ID für den Standort wird intern zum Nachverfolgen von Positionen im Code durch die DE verwendet und ist in der Regel eine Adresse oder einen Offset zufallswertemodul produzierte. Die einzige Anforderung ist, dass Code Rahmen Speicherorten kleiner Rahmen Code einem anderen Speicherort ist dann der entsprechenden Code-ID für die Standort des ersten Codekontext auch kleiner als der Speicherort des zweiten Code Kontexts Bezeichner sein muss.  
  
 Um im Rahmen von Code für eine ID für den Standort Code abzurufen, rufen Sie die [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)