---
title: 'IDebugReference2:: GetParent | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetParent
helpviewer_keywords:
- IDebugReference2::GetParent
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 906a4dd5e8bf3b6b50fbd4288440bc2c85c92a22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155861"
---
# <a name="idebugreference2getparent"></a>IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den übergeordneten Verweis eines Verweises ab. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppParent`  
 vorgenommen Gibt ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt zurück, das das übergeordnete Element dieser Eigenschaft darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
