---
title: IDebugDisassemblyStream2::Seek | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 375ff5c08c481061d217fbb0b3a4fac38d1e74c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896639"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Verschiebt des lesezeigers im Disassemblyfenster Stream einer bestimmten Anzahl von Anweisungen, die relativ zur angegebenen Position.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSeekStart`  
 [in] Ein Wert aus der [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) Enumeration, der angibt, der die relative Position, um die Suche zu starten.  
  
 `pCodeContext`  
 [in] Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das den Codekontext, der der Suchvorgang relativ ist darstellt. Dieser Parameter wird verwendet, nur dann, wenn `dwSeekStart`  =  `SEEK_START_CODECONTEXT`ist, andernfalls dieser Parameter wird ignoriert, und kann ein null-Wert sein.  
  
 `uCodeLocationId`  
 [in] Der Bezeichner der Code-Speicherort, dem der Suchvorgang relativ ist. Dieser Parameter wird verwendet, wenn `dwSeekStart`  =  `SEEK_START_CODELOCID`ist, andernfalls dieser Parameter wird ignoriert, und kann auf 0 festgelegt werden. Finden Sie im Abschnitt "Hinweise" der [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) -Methode für eine Beschreibung der Codebezeichner Speicherort.  
  
 `iInstructions`  
 [in] Die Anzahl der Anweisungen zum Verschieben von relativ zur Position im angegebenen `dwSeekStart`. Dieser Wert kann negativ, zurückzugehen sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` war die Suchposition an eine Stelle außerhalb der Liste der verfügbaren Anweisungen. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 War das an eine Position vor dem Anfang der Liste, ist die erste Anweisung in der Liste die Leseposition fest. Wenn eine Position nach dem Ende der Liste der finden Sie unter war, wird die Leseposition bis zum letzten Anweisung in der Liste festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)