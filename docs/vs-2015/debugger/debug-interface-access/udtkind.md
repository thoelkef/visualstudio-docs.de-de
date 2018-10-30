---
title: UdtKind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c4df2109c2758cdbe21d05375be1e50045cbf4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886649"
---
# <a name="udtkind"></a>UdtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beschreibt die verschiedenen benutzerdefinierten Typ (UDT) an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Elements  
 UdtStruct  
 UDT ist eine Struktur.  
  
 UdtClass  
 UDT ist eine Klasse.  
  
 UdtUnion  
 UDT ist eine Union.  
  
 UdtInterface  
 UDT ist eine Schnittstelle.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch die [idiasymbol:: Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)



