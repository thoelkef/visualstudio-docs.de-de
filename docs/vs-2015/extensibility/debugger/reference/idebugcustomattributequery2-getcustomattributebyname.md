---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft-Dokumentation
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
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80e67c26924a906cada5dec022b8a385f0f4afad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796115"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die benutzerdefinierten Attribute Bytes, die den Namen des benutzerdefinierten Attributs ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCustomAttributeName`  
 [in] Eine Zeichenfolge, die mit dem Namen des zu suchenden benutzerdefinierten Attributs.  
  
 `ppBlob`  
 [in, out] Ein Array, das mit die benutzerdefinierten Attributdaten gefüllt ist.  
  
 `pdwLen`  
 [in, out] Gibt die maximale Anzahl der Bytes, die in Zurückgeben der `ppBlob` array und gibt die Anzahl der tatsächlich in das Array geschriebenen Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn das benutzerdefinierte Attribut nicht vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Legen Sie die `ppBlob` Parameter, um einen null-Wert die Anzahl der zurückzugebenden Attribute verfügbaren Bytes. Anschließend ordnen Sie ein Array, und übergeben Sie dieses Array in für die `ppBlob` Parameter.  
  
 Die Attribut-Bytes stellen die unformatierten Daten des benutzerdefinierten Attributs dar.  
  
 Wenn die `ppBlob` und `pdwLen` Parameter auf einen null-Wert festgelegt sind, diese Methode kann verwendet werden, um zu bestimmen, ob das benutzerdefinierte Attribut lediglich vorhanden ist. Eine einfachere Alternative ist, ist jedoch zum Aufrufen der [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

