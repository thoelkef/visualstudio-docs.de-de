---
title: "IDiaSymbol::get_backEndMinor | Microsoft Docs"
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
  - "IDiaSymbol::get_backEndMinor-Methode"
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Nebenversionsnummer der Back-End des Compilers ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Nummer der Nebenversion Back-End. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Bei erfolgreicher Ausführung gibt `S_OK`andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein Compiler besteht in der Regel zwei Hauptelemente: Front-End (Parser), der analysiert den Quellcode in einem Zwischenformat behandelt und eine Back-End (Codegenerator), das Zwischenformat in Assembly konvertiert. Es ist nicht ungewöhnlich, dass front-End für eine andere Version als Back-End verfügen.  
  
 Ein Front-End oder Back-End-Versionsnummer besteht aus drei Teilen: \< wichtigen>. \< Nebenversion>. \< erstellen>, wobei \< wichtige> ist die Hauptversionsnummer \< kleinere> ist die Nummer der Nebenversion, und \< erstellen> die Buildnummer. Beispielsweise 13.10.3077.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)