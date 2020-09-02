---
title: 'Idebugcustomattribute:: getattributebytes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7813e8e3131b04dc7174b5b666950dd68a6060a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569067"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Attributinformationen als ein BLOB von Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppBlob`  
 [in, out] Ein Array, das mit dem Attribut Bytes gefüllt ist.  
  
 `pdwLen`  
 [in, out] Gibt die maximale Anzahl von Bytes an, die im Array zurückgegeben werden sollen, `ppBlob` und gibt die Anzahl der Bytes zurück, die tatsächlich in das Array geschrieben wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Legen Sie den- `ppBlob` Parameter auf einen NULL-Wert fest, um die Anzahl der verfügbaren Bytes zurückzugeben. Weisen Sie dann ein Array zu, und übergeben Sie das Array für den `ppBlob` Parameter.  
  
 Die Attribut Bytes stellen die Rohdaten des benutzerdefinierten Attributs dar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
