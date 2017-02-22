---
title: "IDiaSession::findLinesByRVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::findLinesByRVA-Methode"
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLinesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Zeilen in einer bestimmten Kompiliereinheit ab, das eine angegebene relative virtuelle Adresse \(RVA\) enthalten.  
  
## Syntax  
  
```cpp#  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `rva`  
 \[in\]  Gibt die Adresse als RVA an.  
  
 `length`  
 \[in\]  Gibt die Anzahl der Bytes Adressbereich an, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)\-Objekt zurück, das eine Liste aller Zeilennummern enthält, die mit dem angegebenen Adressbereich enthalten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 In diesem Beispiel wird eine Funktion veranschaulicht, die alle Zeilennummern erhält, die in der angegebenen Funktion mit der relativen virtuellen Adresse der Funktion und der Länge.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                rva;  
    ULONGLONG            length;  
  
    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)