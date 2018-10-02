---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59f30cae879b1769e120fcdc2852a75f88f2f2bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511017"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCoreServer3::GetServerFriendlyName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname).  
  
Ruft einen Anzeigenamen für den Server ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 [out] Gibt einen Anzeigenamen für den Server zurück.  
  
> [!NOTE]
>  Der Aufrufer ist verantwortlich für das Freigeben der Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Für Benutzer-gestartet-Server ist der Name, der von dieser Methode zurückgegebene den vollständigen Namen des Servers. Bei Servern automatisch gestartet werden ist der Name des Computers an den Server ausgeführt wird, auf.  
  
 Rufen Sie für den Namen der Computer-orientierten der [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)

