---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 09b415e01b6c768f471bdf9ad2e595d1a910d582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Ruft den Bereich für die aktuelle Dokumentposition ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwBegOffset`  
 [in, out] Offset für die Startposition des Bereichs. Legen Sie diesen Parameter auf den Wert null, wenn diese Informationen nicht benötigt wird.  
  
 `pdwEndOffset`  
 [in, out] Offset für die Endposition des Bereichs. Legen Sie diesen Parameter auf den Wert null, wenn diese Informationen nicht benötigt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In einem Dokumentposition für einen Positionshaltepunkt angegebene Bereich werden vom Debugging-Modul (DE) für eine Anweisung voraus suchen, die tatsächlich Code beiträgt. Beachten Sie z. B. folgenden Code:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Zeile 5 trägt dazu bei keinen Code für das Programm, das gerade gedebuggt wird. Wenn der Debugger, der den Haltepunkt in Zeile 5 festlegt die DE möchte um eine bestimmte Menge für die erste Zeile vorwärts zu suchen, die Code beiträgt, würde der Debugger einen Bereich angeben, der weitere Kandidat Zeilen enthält, in denen ein Haltepunkt ordnungsgemäß eingefügt werden kann. DE würde dann vorwärts durch die Zeilen suchen, bis er eine Zeile gefunden, die einen Haltepunkt akzeptieren konnte.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)