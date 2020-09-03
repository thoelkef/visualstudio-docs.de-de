---
title: 'Idebugmethodfield:: enumalllocals | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190891"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für alle lokalen Variablen der Methode, einschließlich derjenigen, die intern von einem Compiler generiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 in Ein [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt, das eine debugadresse innerhalb der Methode darstellt, die auf einen bestimmten Bereich oder Kontext verweist.  
  
 `ppLocals`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste aller lokalen Variablen im angegebenen Bereich darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, der keine lokalen Variablen angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine lokalen vorhanden sind Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Nur die Variablen, die in dem Block definiert sind, der die angegebene debugadresse enthält, werden aufgezählt. Diese Methode schließt alle vom Compiler generierten lokalen Variablen ein. Wenn nur die lokalen Variablen in der Quelle explizit definiert sind, müssen Sie die [enumlocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) -Methode aufzurufen.  
  
 Eine Methode kann mehrere Bereichs bezogene Kontexte oder Blöcke enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
