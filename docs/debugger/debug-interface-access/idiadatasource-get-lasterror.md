---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "IDiaDataSource::get_lastError-Methode"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Dateinamen für den letzten Ladefehler ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Parameter  
 pRetVal  
 \[out\]  Gibt eine Zeichenfolge zurück, die den .pdb\-Dateinamen enthält, der dem letzten Ladefehler zugeordnet ist.  
  
## Rückgabewert  
 Gibt den letzten Fehlercode zurück, der durch einen Ladevorgang verursacht wurde.  Gibt `E_INVALIDARG` zurück, wenn der Parameter `pRetVal``NULL`ist.  
  
## Beispiel  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)