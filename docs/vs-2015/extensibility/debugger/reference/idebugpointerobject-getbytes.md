---
title: IDebugPointerObject::GetBytes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223b71d37094bf8bd16e906905383ffeaf030212
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176331"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Wert als eine Reihe von aufeinander folgenden Bytes gezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwStart`  
 [in] Ein Offset in Bytes vom Beginn des Objekts auf den verwiesen wird.  
  
 `dwCount`  
 [in] Die Anzahl der abzurufenden Bytes.  
  
 `pBytes`  
 [in, out] Ein Array, das mit dem Wert als eine Reihe von aufeinander folgenden Bytes gefüllt ist, auf die am angegebenen Offset aus dem Objekt ab.  
  
 `pdwBytes`  
 [out] Gibt die Anzahl der Bytes, die tatsächlich abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, wenn der Zeiger, dargestellt durch diese [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) verweist auf einen primitiven Typ oder einem einfachen Array primitiver Typen (d. h. ein Array, das durch eine einfache Folge von Bytes dargestellt werden können).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)

