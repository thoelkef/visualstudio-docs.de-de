---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2725eb876cf66665c27027dd4d9b250ed7e866e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Verschiebt den schreibgeschützten Zeiger im Disassembly-Datenstrom einer bestimmten Anzahl von Anweisungen relativ zu einer angegebenen Position.  
  
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
 [in] Ein Wert aus der [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) Enumeration, der angibt, der die relative Position, um die Suche zu beginnen.  
  
 `pCodeContext`  
 [in] Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das den Codekontext, der der Suchvorgang ist darstellt. Dieser Parameter wird nur verwendet, wenn `dwSeekStart`  =  `SEEK_START_CODECONTEXT`ist, andernfalls dieser Parameter wird ignoriert, und kann ein null-Wert sein.  
  
 `uCodeLocationId`  
 [in] Der Bezeichner der Code-Speicherort, dem der Suchvorgang ist. Dieser Parameter wird verwendet, wenn `dwSeekStart`  =  `SEEK_START_CODELOCID`ist, andernfalls dieser Parameter wird ignoriert, und kann auf 0 festgelegt werden. Finden Sie im Abschnitt "Hinweise" für die [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) Methode, eine Beschreibung ein Code-Position-Bezeichner.  
  
 `iInstructions`  
 [in] Die Anzahl der Anweisungen, die relativ zur Position im angegebenen verschieben `dwSeekStart`. Dieser Wert kann rückwärts verschieben negativ sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` war die Seek-Position an eine Stelle hinter der Liste der verfügbaren Anweisungen. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn das an eine Position vor dem Anfang der Liste war, wird die Leseposition für die erste Anweisung in der Liste festgelegt. Wenn die ausführliche Informationen finden Sie an eine Position nach dem Ende der Liste war, wird die Leseposition bis zum letzten Anweisung in der Liste festgelegt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)