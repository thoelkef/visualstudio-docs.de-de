---
title: 'IDebugDisassemblyStream2:: getcodecontext | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a98840982d44c2ee2348ca5c321d08cc6c46ffc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196243"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt ein Code Kontext Objekt zurück, das einem angegebenen Bezeichner für den Code Speicherort entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `uCodeLocationId`  
 in Gibt den Bezeichner des Code Speicher Orts an. Eine Beschreibung eines Code Speicherort Bezeichners finden Sie im Abschnitt "Hinweise" der Methode " [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) ".  
  
 `ppCodeContext`  
 vorgenommen Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt zurück, das den zugeordneten Code Kontext darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Bezeichner für den Code Speicherort kann von einem Rückruf der [getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) -Methode zurückgegeben werden und kann in der [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) -Struktur vorkommen.  
  
 Um einen Code Kontext in einen Bezeichner für den Code Speicherort zu konvertieren, müssen Sie die [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) -Methode aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [Getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [Getcurrentlocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
