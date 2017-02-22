---
title: "IDiaSession::findLinesByLinenum | Microsoft Docs"
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
  - "IDiaSession::findLinesByLinenum-Methode"
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bestimmt die Zeilennummern der Kompiliereinheit sicher, dass die angegebene Zeilennummer in einer Quelldatei Elemente befindet oder nähert.  
  
## Syntax  
  
```cpp#  
HRESULT findLinesByLinenum (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `compiland`  
 \[in\]  Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das die Kompiliereinheit darstellt, in der für die Zeilennummern suchen.  Dieser Parameter darf nicht `NULL` sein.  
  
 `file`  
 \[in\]  Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekt, das die Quelldatei darstellt, das gesucht werden soll.  Dieser Parameter darf nicht `NULL` sein.  
  
 `linenum`  
 \[in\]  Gibt eine 1\-basierte Zeilennummer an.  
  
> [!NOTE]
>  Sie können keine nicht verwenden, um alle Zeilen anzugeben \(verwenden Sie die [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)\-Methode, um alle Zeilen zu suchen\).  
  
 `column`  
 \[in\]  Gibt die Nummer der Spalte an.  Verwendung von Nullen, alle Spalten anzugeben.  Eine Spalte ist ein Byteoffset in eine Zeile.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta zurück, das eine Liste der abgerufenen Zeilennummern enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie eine Quelldatei öffnet, die Kompiliereinheiten auflistet, die durch diese Datei bereitgestellt werden und die Zeilennummern in der Quelldatei in der jeder Kompiliereinheit beginnt.  
  
```cpp#  
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)  
{  
    IDiaEnumSourceFiles* pEnum;  
    IDiaSourceFile*      pFile;  
    DWORD                celt;  
  
    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );  
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file  
    {  
        IDiaEnumSymbols* pEnumCompilands;  
        IDiaSymbol* pCompiland;  
  
        pFile->get_compilands ( &pEnumCompilands );  
        // for each compiland  
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )  
        {  
            IDiaEnumLineNumbers* pEnum;  
            // Find first compiland closest to line 1 of the file.  
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)  
            {  
                IDiaLineNumber *pLineNumber;  
                DWORD lineCount;  
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)  
                {  
                     DWORD lineNum;  
                     if (pLineNumber->get_line(&lineNum) == S_OK)  
                     {  
                          printf("compiland starts in source at line number = %lu\n",lineNum);  
                     }  
                }  
            }  
        }  
    }  
}  
```  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)