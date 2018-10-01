---
title: UsingNameSpace | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- UsingNamespace symbol tag
ms.assetid: e8e1beb5-7cb9-43b4-9ff4-760d5f91ea2d
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbedc0fa1c718bf45472fa29309fa5d460c1c001
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522734"
---
# <a name="usingnamespace"></a>UsingNameSpace
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [UsingNameSpace](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/usingnamespace).  
  
Einige Symbole möglicherweise vom Namespace bezeichnet werden, und würden anschließend identifiziert werden eine `SymTagUsingNameSpace` Tag.  
  
> [!NOTE]
>  UsingNamespace-Symboltag wird nur in verwaltetem Code.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die einschließende Kompiliereinheit, blockieren oder Funktion.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Namespace-Name.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagNameSpace` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
  
## <a name="see-also"></a>Siehe auch  
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



