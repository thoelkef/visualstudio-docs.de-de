---
title: "CvIsEnabled-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled-Methode"
  - "CvIsEnabledEx-Methode"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvIsEnabled-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmt, ob eine Sitzung den festgelegten ETW\-Anbieter aktiviert hat.  
  
## Syntax  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### Parameter  
 `category`  
 Kategorie.  
  
 `level`  
 Wichtigkeitsstufe.  
  
 `pProvider`  
 Gültiges Anbieterobjekt.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn Anbieter nur aktiviert ist.  S\_FALSE Anbieter, wenn gerade deaktiviert wird.  Fehlercode, sofern dieses alle Fehler auftritt.  Verwenden Sie AUSFALLEN Makro, um auf Fehlerzustand und dann sicherzustellen für S\_OK\/S\_FALSE zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)