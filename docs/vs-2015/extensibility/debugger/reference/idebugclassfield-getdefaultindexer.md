---
title: 'Idebugclassfield:: getdefaultindexer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6be0a1925a1e5d48941c1c0e13ac1b4789687229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191022"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen des Standardindexers ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrIndexer`  
 vorgenommen Gibt eine Zeichenfolge zurück, die den Namen des Standardindexers enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben oder S_FALSE zurückgegeben, wenn kein Standardindexer vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standardindexer einer Klasse ist die Eigenschaft, die als `Default` Eigenschaft für Array Zugriffe gekennzeichnet ist. Dies ist spezifisch für [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] . Im folgenden finden Sie ein Beispiel für einen in deklarierten Standardindexer [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] und seine Verwendung.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
