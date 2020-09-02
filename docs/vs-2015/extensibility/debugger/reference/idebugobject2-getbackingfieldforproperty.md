---
title: 'IDebugObject2:: getbackingfieldforproperty | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536385"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft das Feld oder die Variable (sofern vorhanden) ab, die möglicherweise die von diesem-Objekt dargestellte Eigenschaft unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppObject`  
 vorgenommen Ein [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) -Objekt, das das Unterstützungs Feld beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Das [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) -Objekt stellt eine Eigenschaft der verwalteten Code Klasse dar, d. h. eine Methode mit einem Get-und/oder Set-Accessor. Diese Eigenschaften erfordern im Allgemeinen, dass eine Variable den von der-Eigenschaft bearbeiteten Wert enthält. Diese Variable wird als dahinter liegendes Feld bezeichnet. Wenn kein dahinter liegendes Feld für das Objekt vorhanden ist, stellen Sie sicher, dass Sie einen NULL-Wert zurückgeben: einige Aufrufer achten möglicherweise nicht auf den Rückgabewert, sondern sehen stattdessen, ob ein NULL-Wert in zurückgegeben wurde `ppObject` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
