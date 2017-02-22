---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType-Methode"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Typ der Prüfsummen ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt den Typ der Prüfsummen zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Typ der Prüfsummen ist ein Wert, der in einen Prüfsummenalgorithmus zugeordnet werden kann.  Beispielsweise kann das Dateiformat des Standards PDB einen der folgenden Werte haben: i. d. R.  
  
|Prüfsummen\-Typ|CryptoAPI\-Bezeichnung|Beschreibung|  
|---------------------|----------------------------|------------------|  
|0|\<Keine\>|Kein Prüfsummen vorhanden ist.|  
|1|`CALG_MD5`|Prüfsumme wird mit dem Hashalgorithmus MD5.|  
|2|`CALG_SHA1`|Prüfsumme wird mit dem SHA1\-Hashalgorithmus.|  
  
 Die `CryptoAPI` Bezeichnungen sind von der `ALG_ID`\-Enumeration.  Weitere Informationen über die Verwendung in Hashalgorithmen `CryptoAPI` , lesen Sie den Abschnitt Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Zum Abrufen der eigentlichen Prüfsummen Bytes für die Quelldatei, rufen Sie die [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)\-Methode auf.  
  
## Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)