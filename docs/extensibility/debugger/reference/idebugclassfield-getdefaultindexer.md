---
title: "IDebugClassField::GetDefaultIndexer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetDefaultIndexer"
helpviewer_keywords: 
  - "IDebugClassField::GetDefaultIndexer-Methode"
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des standardmäßigen Indexers ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```c#  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### Parameter  
 `pbstrIndexer`  
 \[out\]  Gibt eine Zeichenfolge zurück, die den Namen des standardmäßigen Indexers enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn kein Standardindexer vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Standardindexer einer Klasse ist die Eigenschaft gekennzeichnet ist, während die `Default`\-Eigenschaft für Arrays veranschaulicht.  Dies ist mit [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]bestimmt.  Im Folgenden finden Sie ein Beispiel für einen standardmäßigen Indexers, der in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] deklariert wird und wie er verwendet wird.  
  
```vb#  
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
  
## Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)