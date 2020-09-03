---
title: SymTagEnum | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1578d88265769414f68964e28d3426ffcc62f9e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193519"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Typ des Symbols an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elemente  
 `SymTagNull`  
 Gibt an, dass das Symbol keinen Typ aufweist.  
  
 `SymTagExe`  
 Gibt an, dass das Symbol eine exe-Datei ist. Es gibt nur ein `SymTagExe` Symbol pro Symbol Speicher. Er fungiert als globaler Bereich und verfügt über kein lexikalisches übergeordnetes Element.  
  
 `SymTagCompiland`  
 Gibt das compilersymbol für jede Compilerkomponente des Symbol Speicher an. Für native Anwendungen `SymTagCompiland` entsprechen Symbole den Objektdateien, die mit dem Bild verknüpft sind. Für einige Arten von Microsoft Intermediate Language (MSIL)-Images gibt es eine compilerklasse pro Klasse.  
  
 `SymTagCompilandDetails`  
 Gibt an, dass das Symbol Erweiterte Attribute von compiland enthält. Das Abrufen dieser Eigenschaften erfordert möglicherweise das Laden von compilund Symbolen.  
  
 `SymTagCompilandEnv`  
 Gibt an, dass das Symbol eine Umgebungs Zeichenfolge ist, die für das Kompilieren definiert ist.  
  
 `SymTagFunction`  
 Gibt an, dass das Symbol eine Funktion ist.  
  
 `SymTagBlock`  
 Gibt an, dass das Symbol ein Block ist.  
  
 `SymTagData`  
 Gibt an, dass das Symbol Daten ist.  
  
 `SymTagAnnotation`  
 Gibt an, dass das Symbol für eine Code Anmerkung gilt. Untergeordnete Elemente dieses Symbols sind konstante Daten Zeichenfolgen ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). Diese Symbole werden von den meisten Clients ignoriert.  
  
 `SymTagLabel`  
 Gibt an, dass das Symbol eine Bezeichnung ist.  
  
 `SymTagPublicSymbol`  
 Gibt an, dass das Symbol ein öffentliches Symbol ist. Bei nativen Anwendungen ist dieses Symbol das externe COFF-Symbol, das beim Verknüpfen des Bilds aufgetreten ist.  
  
 `SymTagUDT`  
 Gibt an, dass das Symbol ein benutzerdefinierter Typ (Struktur, Klasse oder Union) ist.  
  
 `SymTagEnum`  
 Gibt an, dass das Symbol eine Enumeration ist.  
  
 `SymTagFunctionType`  
 Gibt an, dass das Symbol ein Funktions Signatur Typen ist.  
  
 `SymTagPointerType`  
 Gibt an, dass das Symbol ein Zeigertyp ist.  
  
 `SymTagArrayType`  
 Gibt an, dass das Symbol ein Arraytyp ist.  
  
 `SymTagBaseType`  
 Gibt an, dass das Symbol ein Basistyp ist.  
  
 `SymTagTypedef`  
 Gibt an, dass das Symbol ein ist, d `typedef` . h. ein Alias für einen anderen Typ.  
  
 `SymTagBaseClass`  
 Gibt an, dass das Symbol eine Basisklasse eines benutzerdefinierten Typs ist.  
  
 `SymTagFriend`  
 Gibt an, dass das Symbol ein Freund eines benutzerdefinierten Typs ist.  
  
 `SymTagFunctionArgType`  
 Gibt an, dass das Symbol ein Funktions Argument ist.  
  
 `SymTagFuncDebugStart`  
 Gibt an, dass das Symbol die Endposition des prologcodes der Funktion ist.  
  
 `SymTagFuncDebugEnd`  
 Gibt an, dass das Symbol die Anfangsposition des epilogcodes der Funktion ist.  
  
 `SymTagUsingNamespace`  
 Gibt an, dass das Symbol ein Namespace Name ist, der im aktuellen Bereich aktiv ist.  
  
 `SymTagVTableShape`  
 Gibt an, dass das Symbol eine virtuelle Tabellen Beschreibung ist.  
  
 `SymTagVTable`  
 Gibt an, dass das Symbol ein virtueller Tabellen Zeiger ist.  
  
 `SymTagCustom`  
 Gibt an, dass das Symbol ein benutzerdefiniertes Symbol ist und nicht von Dia interpretiert wird.  
  
 `SymTagThunk`  
 Gibt an, dass das Symbol ein Thunk ist, der zum Freigeben von Daten zwischen 16 und 32 Bit-Code verwendet wird.  
  
 `SymTagCustomType`  
 Gibt an, dass das Symbol ein benutzerdefiniertes compilersymbol ist.  
  
 `SymTagManagedType`  
 Gibt an, dass das Symbol in den Metadaten angegeben ist.  
  
 `SymTagDimension`  
 Gibt an, dass das Symbol ein mehrdimensionales Fortran-Array ist.  
  
 `SymTagCallSite`  
 Gibt an, dass das Symbol die CallSite darstellt.  
  
 `SymTagInlineSite`  
 Gibt an, dass das Symbol die Inline Site darstellt.  
  
 `SymTagBaseInterface`  
 Gibt an, dass das Symbol eine Basisschnittstelle ist.  
  
 `SymTagVectorType`  
 Gibt an, dass das Symbol ein Vector-Typ ist.  
  
 `SymTagMatrixType`  
 Gibt an, dass das Symbol ein Matrix-Typ ist.  
  
 `SymTagHLSLType`  
 Gibt an, dass das Symbol ein allgemeiner Shader-Sprachtyp ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Symbole in einer Debugdatei verfügen über ein identifizierendes Tag, das den Typ des Symbols angibt.  
  
 Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -Methode zurückgegeben.  
  
 Die Werte in dieser Enumeration werden an die folgenden Methoden übermittelt, um den Suchbereich auf einen bestimmten Symboltyp zu begrenzen:  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Lexikalische Hierarchie von Symbol Typen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession:: findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession:: findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession:: findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession:: findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession:: findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession:: findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
