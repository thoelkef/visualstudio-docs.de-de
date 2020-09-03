---
title: 'IDebugDocumentText2:: GetSize | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6d438db999e2e0b2aa85c45c0b38333238755e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200212"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Größe des Texts an dieser Position im Dokument ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcNumLines`  
 vorgenommen Gibt die Anzahl von Textzeilen zurück.  
  
 `pcNumChars`  
 vorgenommen Gibt die Anzahl von Textzeichen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 [Nur C++] Wenn ein bestimmter Wert nicht erwünscht ist, übergeben Sie einen NULL-Wert für den-Parameter.  
  
 [Nur c#] Beide Parameter müssen angegeben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
