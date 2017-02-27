---
title: "IDiaSession::findLinesByAddr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findLinesByAddr-Methode"
ms.assetid: 640403c0-14cf-403c-ad19-38b3bdc28ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::findLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Zeilen in einer bestimmten Kompiliereinheit ab, die einer angegebenen Adresse enthalten.  
  
## Syntax  
  
```cpp#  
HRESULT findLinesByAddr (   
   DWORD                 seg,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `seg`  
 \[in\]  Gibt die Stammkomponente Abschnitts der spezifischen Adresse auf.  
  
 `offset`  
 \[in\]  Gibt die Stammkomponente Offset der spezifischen Adresse an.  
  
 `length`  
 \[in\]  Gibt die Anzahl der Bytes Adressbereich an, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)\-Objekt zurück, das eine Liste aller Zeilennummern enthält, die mit dem angegebenen Adressbereich enthalten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 In diesem Beispiel wird eine Funktion veranschaulicht, die alle Zeilennummern erhält, die in einer Funktion mit der Adresse und der Länge der Funktion enthalten sind.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByAddr(IDiaSymbol *pFunc,  
                                          IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                seg;  
    DWORD                offset;  
    ULONGLONG            length;  
  
    if (pFunc->get_addressSection ( &seg ) == S_OK &&  
        pFunc->get_addressOffset ( &offset ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByAddr( seg, offset, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)