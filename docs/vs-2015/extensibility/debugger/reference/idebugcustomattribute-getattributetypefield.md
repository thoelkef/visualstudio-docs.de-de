---
title: 'Idebugcustomattribute:: getattributetypefield | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a56a148342eb659a4f57d68581159f64ee3b1226
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568925"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Typ der benutzerdefinierten Attribut Klasse ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCAType`  
 vorgenommen Gibt das [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das die Klasse darstellt, von der das benutzerdefinierte Attribut eine Instanz ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode ermöglicht den Zugriff auf ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das diese Klasse beschreibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugcustomattribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
