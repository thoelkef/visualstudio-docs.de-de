---
title: "IDiaSession::getEnumTables | Microsoft Docs"
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
  - "IDiaSession::getEnumTables-Methode"
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::getEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Enumerator für alle Tabellen ab, die im Symbolspeicher enthalten sind.  
  
## Syntax  
  
```cpp#  
HRESULT getEnumTables (   
   IDiaEnumTables** ppEnumTables  
);  
```  
  
#### Parameter  
 `ppEnumTables`  
 \[out\]  Gibt ein [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)\-Objekt zurück.  Verwenden Sie diese Schnittstelle, um die Tabellen im Symbolspeicher aufzulisten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Dieses Beispiel stellt eine allgemeine Funktion dar, die die `getEnumTables`\-Methode verwendet, um ein bestimmtes Enumeratorobjekt.  Wenn dieser gefunden wird, gibt die Funktion einen Zeiger zurück, der auf die gewünschte Schnittstelle umgewandelt werden kann. andernfalls gibt die Funktion `NULL`zurück.  
  
```cpp#  
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)  
{  
    IUnknown *pUnknown = NULL;  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumTables> pEnumTables;  
        if (pSession->getEnumTables(&pEnumTables) == S_OK)  
        {  
             CComPtr<IDiaTable> pTable;  
             DWORD celt = 0;  
             while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&  
                   celt == 1)  
             {  
                  if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)  
                  {  
                       break;  
                  }  
                  pTable = NULL;  
             }  
        }  
    }  
    return(pUnknown);  
}  
```  
  
## Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)