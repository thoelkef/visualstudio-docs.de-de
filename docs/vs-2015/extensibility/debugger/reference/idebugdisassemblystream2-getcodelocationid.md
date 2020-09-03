---
title: 'IDebugDisassemblyStream2:: getcodelta-ID | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebb2280f814985e2352413921a00268d96761b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196228"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt einen Bezeichner für den Code Speicherort für einen bestimmten Code Kontext zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das in einen Bezeichner konvertiert werden soll.  
  
 `puCodeLocationId`  
 vorgenommen Gibt den Bezeichner des Code Speicher Orts zurück. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_CODE_CONTEXT_OUT_OF_SCOPE` Wenn der Code Kontext gültig, aber außerhalb des Bereichs ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Bezeichner für den Code Speicherort ist für die Debug-Engine (de) spezifisch, die die Disassembly unterstützt Dieser Speicherort Bezeichner wird intern von der de verwendet, um Positionen im Code zu verfolgen, und ist in der Regel eine Adresse oder ein Offset. Die einzige Voraussetzung ist, dass der Code Kontext eines Speicher Orts, der kleiner als der Code Kontext einer anderen Position ist, auch kleiner als der Bezeichner für den Code Speicherort des zweiten Code Kontexts sein muss.  
  
 Um den Code Kontext eines Code Speicherort Bezeichners abzurufen, rufen Sie die [getcodecontext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) -Methode auf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
