---
title: IDebugCoreServer3::GetServerFriendlyName | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa81daf7ab1d592e6a2cd460268e5d66925f61e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445269"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft einen Anzeigenamen für den Server ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrName`  
 [out] Gibt einen Anzeigenamen für den Server zurück.  
  
> [!NOTE]
> Der Aufrufer ist verantwortlich für das Freigeben der Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Für Benutzer-gestartet-Server ist der Name, der von dieser Methode zurückgegebene den vollständigen Namen des Servers. Bei Servern automatisch gestartet werden ist der Name des Computers an den Server ausgeführt wird, auf.  
  
 Rufen Sie für den Namen der Computer-orientierten der [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
