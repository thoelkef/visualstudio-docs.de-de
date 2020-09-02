---
title: DataKind | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197632"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den bestimmten Bereich eines Daten Werts an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
## <a name="elements"></a>Elemente  
 DataIsUnknown  
 Das Daten Symbol kann nicht bestimmt werden.  
  
 DataIsLocal  
 Das Datenelement ist eine lokale Variable.  
  
 DataIsStaticLocal  
 Das Datenelement ist eine statische lokale Variable.  
  
 DataIsParam  
 Das Datenelement ist ein formaler Parameter.  
  
 DataIsObjectPtr  
 Das Datenelement ist ein Objekt Zeiger ( `this` ).  
  
 DataIsFileStatic  
 Das Datenelement ist eine Variable mit Datei Bereich.  
  
 DataIsGlobal  
 Das Datenelement ist eine globale Variable.  
  
 DataIsMember  
 Das Datenelement ist eine Objektmember-Variable.  
  
 DataIsStaticMember  
 Das Datenelement ist eine statische Klassen Variable.  
  
 Dataisconstant  
 Das Datenelement ist ein konstanter Wert.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von der [idiasymmetribol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
