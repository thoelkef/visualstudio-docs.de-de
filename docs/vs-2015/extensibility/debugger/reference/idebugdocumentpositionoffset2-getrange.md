---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200228"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Bereich für die aktuelle Dokument Position ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in, out] Offset für die Anfangsposition des Bereichs. Legen Sie diesen Parameter auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
 `pdwEndOffset`  
 [in, out] Offset für die Endposition des Bereichs. Legen Sie diesen Parameter auf einen NULL-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der in einer Dokument Position für einen Location-Breakpoint angegebene Bereich wird von der Debug-Engine (de) verwendet, um nach einer Anweisung zu suchen, die tatsächlich Code beiträgt. Beachten Sie z. B. folgenden Code:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Zeile 5 trägt keinen Code zu dem Programm bei, das gedeppt wird. Wenn der Debugger, der den Breakpoint in Zeile 5 festlegt, eine bestimmte Menge für die erste Zeile, die Code beiträgt, durchsucht, würde der Debugger einen Bereich angeben, der zusätzliche Kandidaten Zeilen enthält, in denen ein Haltepunkt ordnungsgemäß platziert werden kann. Der de würde dann diese Zeilen durchsuchen, bis eine Zeile gefunden wird, die einen Haltepunkt akzeptieren könnte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
