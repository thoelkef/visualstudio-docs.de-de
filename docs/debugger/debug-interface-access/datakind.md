---
title: DataKind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f87fea09976128f57e8c7dca77dcaea839aab4c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879500"
---
# <a name="datakind"></a>DataKind
Gibt an, die bestimmten Bereich eines Datenwerts.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elements  
 DataIsUnknown  
 Symbol "Daten" kann nicht bestimmt werden.  
  
 DataIsLocal  
 Datenelement ist eine lokale Variable.  
  
 DataIsStaticLocal  
 Datenelement ist eine statische lokale Variable.  
  
 DataIsParam  
 Datenelement ist ein formaler Parameter.  
  
 DataIsObjectPtr  
 Datenelement ist einem Zeiger (`this`).  
  
 DataIsFileStatic  
 Datenelement ist eine Variable im Bereich einer Datei.  
  
 DataIsGlobal  
 Datenelement ist eine globale Variable.  
  
 DataIsMember  
 Datenelement ist eine Objektvariable des Elements.  
  
 DataIsStaticMember  
 Datenelement ist eine statische Klasse-Variable.  
  
 DataIsConstant  
 Datenelement ist ein konstanter Wert.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch die [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)