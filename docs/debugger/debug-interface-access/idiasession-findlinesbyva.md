---
title: "IDiaSession::findLinesByVA | Microsoft Docs"
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
  - "IDiaSession::findLinesByVA-Methode"
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Zeilennummerninformationen für die Zeilen ab, die in einem angegebenen Bereich enthaltenen der virtuellen Adresse \(VA\).  
  
## Syntax  
  
```cpp#  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `va`  
 \[in\]  Gibt die Adresse als VA an.  
  
 `length`  
 \[in\]  Gibt die Anzahl der Bytes Adressbereich an, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)\-Objekt zurück, das eine Liste aller Zeilennummern enthält, die mit dem angegebenen Adressbereich enthalten.  
  
## Beispiel  
 In diesem Beispiel wird eine Funktion veranschaulicht, die alle Zeilennummern erhält, die in einer Funktion mit virtuellen Adresse der Funktion und der Länge.  
  
```cpp#  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)