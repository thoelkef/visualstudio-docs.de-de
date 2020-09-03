---
title: 'IDebugDisassemblyStream2:: getcurrentlocation | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCurrentLocation
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 133a46c273fed04ad95bb52076b1d5d172cc0517
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196208"
---
# <a name="idebugdisassemblystream2getcurrentlocation"></a>IDebugDisassemblyStream2::GetCurrentLocation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt einen Bezeichner für den Code Speicherort zurück, der den aktuellen codeort darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCurrentLocation(   
   UINT64* puCodeLocationId  
);  
```  
  
```csharp  
int GetCurrentLocation(   
   out ulong puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `puCodeLocationId`  
 vorgenommen Gibt den Bezeichner des Code Speicher Orts zurück. Eine Beschreibung eines Code Speicherort Bezeichners finden Sie im Abschnitt "Hinweise" der Methode " [getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) ".  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Bezeichner für den Code Speicherort kann durch Aufrufen der [getcodecontext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) -Methode in einen Code Kontext konvertiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [Getcodelta ocationid](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
