---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: d0b9ae5b6b9139715cd28b40dd8eae2294c507a7
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
Gibt die Informationen zu einem Stack-Frame-Objekt abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Member  
 FIF_FUNCNAME  
 Die Initialisierung/verwenden die `m_bstrFuncName` Feld.  
  
 FIF_RETURNTYPE  
 Die Initialisierung/verwenden die `m_bstrReturnType` Feld.  
  
 FIF_ARGS  
 Die Initialisierung/verwenden die `m_bstrArgs` Feld.  
  
 FIF_LANGUAGE  
 Die Initialisierung/verwenden die `m_bstrLanguage` Feld.  
  
 FIF_MODULE  
 Die Initialisierung/verwenden die `m_bstrModule` Feld.  
  
 FIF_STACKRANGE  
 Die Initialisierung/verwenden die `m_addrMin` und `m_addrMax` Felder (Stapel-Bereich).  
  
 FIF_FRAME  
 Die Initialisierung/verwenden die `m_pFrame` Feld.  
  
 FIF_DEBUGINFO  
 Die Initialisierung/verwenden die `m_fHasDebugInfo` Feld.  
  
 FIF_STALECODE  
 Die Initialisierung/verwenden die `m_fStaleCode` Feld.  
  
 FIF_ANNOTATEDFRAME  
 Die Initialisierung/verwenden die `m_fAnnotatedFrame` Feld.  
  
 FIF_DEBUG_MODULEP  
 Die Initialisierung/verwenden die `m_pModule` Feld.  
  
 FIF_FUNCNAME_FORMAT  
 Formatiert den Namen der Funktion an. Das Ergebnis wird zurückgegeben, der `m_bstrFunName` Feld und keine anderen Felder ausgefüllt sind.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Fügt den Rückgabetyp für die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS  
 Fügt die Argumenten, die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_LANGUAGE  
 Fügt die Sprache der `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_MODULE  
 Fügt den Modulnamen, um die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_LINES  
 Fügt die Anzahl von Zeilen, die die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_OFFSET  
 Hinzugefügt, die `m_bstrFuncName` Feld den Offset in Bytes vom Anfang der Zeile, wenn `FIF_FUNCNAME_LINES` angegeben ist. Wenn `FIF_FUNCNAME_LINES` nicht angegeben wird, oder wenn Zeilennummern nicht verfügbar sind, fügt den Offset in Bytes vom Beginn der Funktion.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Fügt den Typ jedes Arguments Funktion, um die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Fügt den Namen des jede Funktionsargument an die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Fügt den Wert jedes Arguments Funktion, um die `m_bstrFuncName` Feld.  
  
 FIF_FUNCNAME_ARGS_ALL  
 Fügt dem Typ, der Name und der Wert von allen Argumenten, die die `m_bstrFuncName` Feld.  
  
 FIF_ARGS_TYPES  
 Die Argumenttypen abgerufen und formatiert.  
  
 FIF_ARGS_NAMES  
 Argumentnamen abgerufen und formatiert.  
  
 FIF_ARGS_VALUES  
 Die Argumentwerte werden abgerufen und formatiert.  
  
 FIF_ARGS_ALL  
 Abgerufen Sie, und formatieren Sie den Typ, Name und Wert für alle Argumente.  
  
 FIF_ARGS_NOFORMAT  
 Gibt an, dass die Argumente sind nicht formatiert (z. B. weder hinzufügen öffnende und schließende Klammern um die Argumentliste enthalten noch ein Trennzeichen zwischen Argumenten hinzufügen).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Gibt an, dass die funktionsauswertung (Eigenschaft) beim Abrufen der Werte für das Argument nicht verwendet werden soll.  
  
 FIF_FILTER_NON_USER_CODE  
 Debugging-Modul werden Nichtbenutzercode Frames zu filtern, sodass sie nicht eingeschlossen werden.  
  
 FIF_ARGS_NO_TOSTRING  
 Nicht zulassen `ToString()` Auswertung oder die Formatierung beim Zurückgeben der Funktionsargumente-Funktion.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Frame-Informationen sollten aus den Hostprozess zugegriffen, anstatt die gehosteten Anwendungsdomäne gelangt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Flags werden zum Übergeben der [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) und [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) Methoden, um anzugeben, welche Felder sind initialisiert werden, in der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder von der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird. Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
