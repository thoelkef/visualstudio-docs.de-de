---
title: "IDiaSession::findInlineeLinesByVA | Microsoft Docs"
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol und Elemente innerhalb der angegebenen virtuellen Adresse \(VA\) enthalten ist.  
  
## Syntax  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,  
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `parent`  
 \[in \]Ein `IDiaSymbol`\-Objekt, das das übergeordnete Objekt darstellt.  
  
 `va`  
 \[in\] Gibt die Adresse als VA an.  
  
 `length`  
 \[in\] gibt den Adressbereich, in Anzahl von Bytes an, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 \[out\] `IDiaEnumLineNumbers` enthält ein Objekt, das die Liste von Zeilennummern enthält, die abgerufen werden.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)