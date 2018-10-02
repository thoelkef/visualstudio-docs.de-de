---
title: IDebugArrayObject2::GetBaseIndices | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4673142d0b9866e36b7a53471406f1808e292aea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522151"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugArrayObject2::GetBaseIndices](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject2-getbaseindices).  
  
Ruft den Basis-Indizes (untere Grenzen) für jeden Index in Anbetracht der Anzahl der Dimensionen im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```csharp  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwRank`  
 [in] Die Anzahl der Dimensionen (Rang) des Arrays.  
  
 `dwIndices`  
 [out] Die Basis Indizes (untere Grenzen) für das Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Beispielsweise würde diese Funktion '5' für das Array erstellt, mit dem folgenden C#-Code zurückgeben:  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)

