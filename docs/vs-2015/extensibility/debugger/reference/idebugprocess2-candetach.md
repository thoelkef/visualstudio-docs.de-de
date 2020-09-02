---
title: 'IDebugProcess2:: candetach | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd96442ad3639aa03fa894facbbc9e6dbe3bbd21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188084"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob der Sitzungs-Debug-Manager (SDM) den Prozess trennen kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben, `S_OK.` `S_FALSE` Wenn der Debugger nicht vom Prozess trennen kann. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Candetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
