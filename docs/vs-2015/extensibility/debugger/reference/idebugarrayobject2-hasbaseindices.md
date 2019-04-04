---
title: IDebugArrayObject2::HasBaseIndices | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- HasBaseIndices
- IDebugArrayObject2::HasBaseIndices
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e9d0c06ad921ad43bcb7a79446062bc6feda8009
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958594"
---
# <a name="idebugarrayobject2hasbaseindices"></a>IDebugArrayObject2::HasBaseIndices
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob das Array Basis Indizes (untere Grenzen) definiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```csharp  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfHasBaseIndices`  
 [out] "True", um anzugeben, dass das Array Basis Indizes (untere Grenzen); hat andernfalls "false".  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.
